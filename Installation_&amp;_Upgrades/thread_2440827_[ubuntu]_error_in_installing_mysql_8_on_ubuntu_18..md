---
title: "[ubuntu] error in installing mysql 8 on ubuntu 18.04"
date: 2020-04-15
forum: Installation &amp; Upgrades
---

### Post by ahmex03 on 2020-04-15
I am trying to install Mysql 8 on my ubuntu 18.04. I uninstalled every previous Mysql installations and make sure there is nothing related to sql on my mchine by executing   ```
$ sudo dpkg -l | grep mysql

```  Next, to install Mysql I issued following commands```


  $ sudo wget https://dev.mysql.com/get/mysql-apt-config_0.8.15-1_all.deb
$ sudo dpkg -i mysql-apt-config_0.8.15-1_all.deb
$ sudo apt-get update

```  all work fine till here, but when I issue this

  ```
$ sudo apt-get install mysql-server

```  I am getting this error. I tried this on two different ubuntu  machines and I am getting same error. Can someone guide what mistake I  am doing?

  ```
    dpkg: error processing package mysql-community-server (--configure):
 installed mysql-community-server package post-installation script subprocess returned error exit status 1
dpkg: dependency problems prevent configuration of mysql-server:
 mysql-server depends on mysql-community-server (= 8.0.19-1ubuntu18.04); however:
  Package mysql-community-server is not configured yet.

dpkg: error processing package mysql-server (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          Processing triggers for man-db (2.8.3-2ubuntu0.1) ...
Processing triggers for libc-bin (2.27-3ubuntu1) ...
Errors were encountered while processing:
 mysql-community-server
 mysql-server
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by mörgæs on 2020-04-16
Already asked here:
[https://askubuntu.com/questions/1227477/error-while-installing-mysql-8-on-ubuntu-18-04](https://askubuntu.com/questions/1227477/error-while-installing-mysql-8-on-ubuntu-18-04)

---

