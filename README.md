# fairyland
A system for OA

说明：
   演示系统所需要的子系统或服务出于方便的目地，全部安装在一台机器中，故对宿主机器配置要求比较高。

   假设宿主机器IP为：192.168.0.107

1. 导入docker镜像

1.1.从本地文件导入docker
sudo docker import fairyland.tar fairyland

1.2 或者从docker仓库导入
sudo docker pull ivantown/fairyland

2.启动docker

sudo docker run --privileged --name fairyland -p 8280:8280 -p 80:80 -p 8888:8888 -p 3478:3478 -p 3478:3478/udp -p 8380:8380 -p 9080:9080 -p 8180:8180 -p 443:443 --rm -d fairyland /sbin/init

3.修改配置文件

3.1 进入docker,执行如下命令
sudo docker exec -it fairyland bash

3.2 找到/root/fairyland/oa_manager/application.oa.manager.properties文件中的im_ip_port和ice_url,将其中的ip换成宿主机器的ip

4.重启oa manager

进入oa manager所在目录(/root/fairyland/oa_manager)后,重启oa manager,重启脚本./restartOaManager.sh

5.使用chrome浏览器访问系统
https://192.168.0.107

