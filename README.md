# site
mysql redis nginx docker镜像配置

### 项目结构
```
.
├── .env            # 默认为dev的环境变量
├── .gitignore
├── .site.js
├── README.md
├── container       # 不同容器的配置文件
│   ├── mysql
│   │   └── docker-compose.yml
│   ├── nginx
│   │   ├── conf
│   │   ├── docker-compose.prod.yml
│   │   └── docker-compose.yml
│   └── redis
│       └── docker-compose.yml
└── prod           # prod的环境变量
    └── .env
```
docker-compose 在运行时会使用当前目录下的.env文件，
并且不支持指定env文件，所以需要多个不同环境时，只能在对应文件夹下建立.env文件
### 启动全部
```
// dev模式
docker-compose up

// prod模式
cd ./prod && docker-compose up

```

### 单独启动
```
docker-compose up nginx
docker-compose up mysql
docker-compose up redis

```

### 运行端口
```
redis 6379:6379
mysql 3306:3306
nginx 80:80
```

### mysql 5.7开启远程连接

```
mysql  -u root -p
use mysql;
GRANT ALL PRIVILEGES ON *.* TO 'root'@'%' IDENTIFIED BY '密码' WITH GRANT OPTION;
FLUSH PRIVILEGES;
```
