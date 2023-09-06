import requests

# 网站登录的URL和用户凭据
login_url = 'https://example.com/login'  # 替换为您的登录页面
username = 'your_username'  # 替换为您的用户名
password = 'your_password'  # 替换为您的密码

# 签到的URL
checkin_url = 'https://example.com/checkin'  # 替换为您的签到页面

# 创建一个会话
session = requests.session()

# 发送登录请求
login_payload = {'username': username, 'password': password}
login_response = session.post(login_url, data=login_payload)

# 检查登录是否成功
if login_response.status_code == 200:
    print('登录成功！')

    # 发送签到请求
    checkin_response = session.get(checkin_url)

    # 检查签到是否成功
    if checkin_response.status_code == 200:
        print('签到成功！')
    else:
        print('签到失败。')

else:
    print('登录失败。')

# 记得关闭会话
session.close()
