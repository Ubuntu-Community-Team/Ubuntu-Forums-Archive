---
title: "Unable to run apt-get with proxy even after setting the environment variables"
date: 2015-04-18
forum: Installation &amp; Upgrades
---

### Post by gopukrishnan on 2015-04-18
Hi all,

I was trying to configure proxy in my lubuntu 14.04. Since I wanted to use the username and password for my proxy authentication, I opted ntlm and installed it. Now I can use my proxy link as 127.0.0.1:3128. Since it is lubuntu, I dont have the gui option to set the proxy system wide as I was doing in the ubuntu machines. After googling, I have found one solution to add the proxy entries in /etc/environment as below :
```
http_proxy=http://127.0.0.1:3128/
https_proxy=http://127.0.0.1:3128/
ftp_proxy=http://127.0.0.1:3128/
no_proxy="localhost,127.0.0.1,localaddress,.localdomain.com"
HTTP_PROXY=http://127.0.0.1:3128/
HTTPS_PROXY=http://127.0.0.1:3128/
FTP_PROXY=http://127.0.0.1:3128/
NO_PROXY="localhost,127.0.0.1,localaddress,.localdomain.com"
```

and created a file named /etc/apt/apt.conf.d/95proxies with the below entries :

```
Acquire::http::proxy "http://127.0.0.1:3128/";
Acquire::ftp::proxy "ftp://127.0.0.1:3128/";
Acquire::https::proxy "https://127.0.0.1:3128/";

```
My issue is now I cant install any packages using the apt-get command.




```
root@test014:~# apt-get install htop
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following NEW packages will be installed:
  htop
0 upgraded, 1 newly installed, 0 to remove and 153 not upgraded.
Need to get 65.3 kB of archives.
After this operation, 203 kB of additional disk space will be used.
Err http://in.archive.ubuntu.com/ubuntu/ utopic/universe htop amd64 1.0.3-1
  407  Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )
E: Failed to fetch http://in.archive.ubuntu.com/ubuntu/pool/universe/h/htop/htop_1.0.3-1_amd64.deb  407  Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )

E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
```








When I checked as user, I can see the proxy entries set in env variable:

```
user1@test014:~$ echo $http_proxy
http://127.0.0.1:3128/

but root usr was showing nothing :

user1@test014:~$ sudo bash
root@test014:~# echo $http_proxy

root@test014:~# exit
```

So I have added the same proxy entries in /etc/bash.bashrc as well and now I can see the env variables from root but still I am not able to run the apt-get commands as root or as normal user using sudo. I think for some reason the 95proxies config file from apt is not fetching correctly. please advise

---

