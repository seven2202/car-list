## 基于chatgpt-share-web外挂list**选车页面**

#### 电脑端界面截图：

![image](https://github.com/seven2202/car-list/assets/111497407/fb24a7d6-69f6-434c-9b3c-51e41736c402)

#### 手机端界面截图：

![image](https://github.com/seven2202/car-list/assets/111497407/29e3d0ec-1d0f-4f1d-a518-b10578eea9f3)

#### 部署教程：

此为打包后的文件

请按照此文档部署

https://chatgpt-share-server.xyhelper.cn/config/list.html

在chatgpt-share新建一个list目录

将打包后的文件置在你的`chatgpt-share/list`目录下。

然后修改`docker-compose.yml`,增加 list 到 volumes 中,例如:

~~~yml
 chatgpt-share-server:
    image: xyhelper/chatgpt-share-server:latest
    restart: always
    ports:
      - 8300:8001
    environment:
      TZ: Asia/Shanghai # 指定时区
      # 接入网关地址
      CHATPROXY: "https://demo.xyhelper.cn"
      # 接入网关的authkey
      AUTHKEY: "xyhelper"
      # 内容审核及速率限制
      AUDIT_LIMIT_URL: "http://auditlimit:8080/audit_limit"
    volumes:
      - ./config.yaml:/app/config.yaml
      - ./data/chatgpt-share-server/:/app/data/
      - ./list:/app/resource/public/list  # 这里增加了list~~~~~~~~~~~~~
    labels:
      - "com.centurylinklabs.watchtower.scope=xyhelper-chatgpt-share-server"
~~~

**然后重启你的docker容器**

**然后重启你的docker容器**

**然后重启你的docker容器**
