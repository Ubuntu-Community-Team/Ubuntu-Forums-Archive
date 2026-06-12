---
title: "Setup up squid as a proxy server"
date: 2009-12-10
forum: Installation &amp; Upgrades
---

### Post by x.knight on 2009-12-10
Dear all 

I have recently installed ubuntu server 9.10 further i want to setup squid as a proxy server and dansguardian as content filter server the scenario is 

i have two lan card in ubuntu server machine one is connected with my local lan subnet 192.168.1.0/24 and other is directly connected to internet its ip is 58.181.97.172/29

i want to configure my local lan is able to run internet via squid server

kindly help me in this regard or provide some totorial and guides to do so

thanks

---

### Post by meghraj.patil on 2011-05-11
Hi,

You need to first configure your eth0 for ur internal LAN and eth1 for your WAN i.e. internet connection should be on it.

Then you need to download squid and dansguardian. 


sudo apt-get install squid

Squid should be configured in following way

Squid should be running on port 3128

should only entertain request from localhost

sudo nano /etc/squid/squid.conf

http_port 3128
acl localhost src 127.0.0.0/255.0.0.0
http_access allow localhost
http_access deny all

-------------------------

sudo apt-get install dansguardian

sudo nano /etc/dansguardian/dansguardian.conf

language = 'ukenglish'
filterip = your proxy server ip
filterport = 8080
proxyip = 127.0.0.1
proxyport = 3128

then save and quit the dansguardian file

sudo /etc/init.d/dansguardian restart
sudo /etc/init.d/squid restart

Now go to you browser ( Mozilla Firefox)
Tools-->Options-->Advance-->Network-->Settings-->Manual Proxy Configuration--> put the proxy server IP eg. 192.168.1.100 and port no. 8080 (i.e. dansguardian port)

Hope it would help you

Meghraj::)

---

