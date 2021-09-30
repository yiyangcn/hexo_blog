---
title: docker安装及常用命令
date: 2021-09-30 15:23:07
tags: [docker]
categories: [服务器运维]
---

# docker安装

参考：[Install Docker Engine on CentOS | Docker Documentation](https://docs.docker.com/engine/install/centos/)

**删除docker（如果第一次安装可略过）**

```shell
sudo yum remove docker \
                  docker-client \
                  docker-client-latest \
                  docker-common \
                  docker-latest \
                  docker-latest-logrotate \
                  docker-logrotate \
                  docker-engine
```

**1.设置docker仓库**

```shell
sudo yum install -y yum-utils
sudo yum-config-manager \
    --add-repo \
https://download.docker.com/linux/centos/docker-ce.repo
```

**2.安装最新版docker**

```shell
sudo yum install docker-ce docker-ce-cli containerd.io
```

或通过下方命令查看版本

```shell
yum list docker-ce --showduplicates | sort -r
docker-ce.x86_64            3:20.10.8-3.el7                    docker-ce-stable
docker-ce.x86_64            3:20.10.8-3.el7                    @docker-ce-stable
docker-ce.x86_64            3:20.10.7-3.el7                    docker-ce-stable
docker-ce.x86_64            3:20.10.6-3.el7                    docker-ce-stable
```

随后用第2列的 `:`和`-`之间的内容 替换`<VERSION String>`的内容，安装对应版本 例如`20.10.8`

```shell
sudo yum install docker-ce-<VERSION String> docker-ce-cli-<VERSION String> containerd.io
```

**3.启动docker**

```shell
sudo systemctl start docker
```

**4.运行镜像测试是否成功**

```shell
sudo docker run hello-world
```

# docker的一些常用命令

参考：[commamline | Docker Documentation](https://docs.docker.com/engine/reference/commandline/docker/)

**搜索镜像**

```shell
docker search python
```

**安装镜像**

```shell
docker pull python:tag
```

**列出安装的镜像**

```shell
docker images
```

**通过镜像运行容器**

`-d`为后台启动 

```shell
docker run --name [给容器命名] -d -p [Linux内部端口号]:[docker内部端口号] python:tag 
```

**进入容器内部**

```
docker exec -it [容器] /bin/bash
```

**查看运行的容器**

```shell
docker ps
```

**删除镜像**

```shell
docker rm [imageName]
```

**docker迁移**

```
# 
```

# 容器备份与恢复

参考：[Back up and restore data | Docker Documentation](https://docs.docker.com/desktop/backup-and-restore/)



```

```

