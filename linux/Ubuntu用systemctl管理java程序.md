### Ubuntu用systemctl管理java程序

1、注册服务

在/etc/systemd/system/ 下新建 **.service

```service
[Unit]
Description=custom
After=syslog.target

[Service]
ExecStart=/usr/bin/java -jar /root/project/custom/custom-mall.jar
Restart=always
StandardOutput=null
LogLevelMax=0

[Install]
WantedBy=multi-user.target
```

2、重新载入systemd，扫描新的或有变动的单元

```
    systemctl daemon-reload
```

3、命令

```
    systemctl status harry-admin #查看服务状态
    systemctl stop harry-admin #停止服务
    systemctl start harry-admin #启动服务
    systemctl reload harry-admin #重新加载
    
    #设置开机自启动:
    systemctl enable harry-admin
    #或
    systemctl enable harry-admin.service
    
    # 又或者不想开机启动:
    systemctl disable harry-admin
    #或
    systemctl disable harry-admin.service
```