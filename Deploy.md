# 进入工作目录
cd /my-eth

# 安装 mysql
```
cd /my-eth

docker run -d --name my-mysql                                    \
      --restart always                                           \
      -p 3306:3306                                               \
      -e MYSQL_ROOT_HOST='%'             `# 开启root的远程访问`  \
      -e MYSQL_ROOT_PASSWORD=56Rt_UUik9e `# root用户的密码`      \
      -e TZ=Asia/Shanghai                `# 设置时区`            \
      -v $PWD/mysql/conf:/etc/mysql/conf.d `#配置文件挂载到当前宿主机的/home/mysql/conf` \
      -v $PWD/mysql/data:/var/lib/mysql    `#数据挂载到当前宿主机的 /home/mysql/data`    \
      mysql:5.7.31                                                \
      --character-set-server=utf8mb4        `# 设置字符编码`      \
      --collation-server=utf8mb4_unicode_ci `# 设置字符编码`      \
      --lower_case_table_names=1            `# 表名不区分大小写`

docker logs -f my-mysql 

```

# 运行 frontend
```
docker run -d --name my-etherscan-explorer -v /my-eth/frontend:/usr/share/nginx/html:ro nginx:1.21.1
```

# 运行 backend
```
docker run -d --name my-etherscan-explorer -v /my-eth/frontend:/usr/share/nginx/html:ro nginx:1.21.1
```

