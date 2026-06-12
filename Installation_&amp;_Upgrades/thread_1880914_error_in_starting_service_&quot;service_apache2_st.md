---
title: "error in starting service &quot;service apache2 start&quot;"
date: 2011-11-14
forum: Installation &amp; Upgrades
---

### Post by prabhas on 2011-11-14
i was tried to install apache2 in my ubuntu 11.10 using the command "sudo apt-get install apache2". It was installed successfully and pops message failed when 

* Starting web server apache2 
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
(98)Address already in use: make_sock: could not bind to address 0.0.0.0:80
no listening sockets available, shutting down
Unable to open logs
Action 'start' failed.
The Apache error log may have more information.
                                                                         [fail]
invoke-rc.d: initscript apache2, action "start" failed.
Setting up apache2 (2.2.20-1ubuntu1.1) ...

 after that i tried 
 apt-get install httpd
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package httpd is a virtual package provided by:
  apache2-mpm-itk 2.2.20-1ubuntu1.1
  apache2-mpm-worker 2.2.20-1ubuntu1.1
  apache2-mpm-prefork 2.2.20-1ubuntu1.1
  apache2-mpm-event 2.2.20-1ubuntu1.1
  yaws 1.90-2
  webfs 1.21+ds1-8
  tntnet 1.6.3-4.1
  thttpd 2.25b-11
  ocsigen 1.3.4-2
  nginx-light 1.0.5-1
  nginx-full 1.0.5-1
  nginx-extras 1.0.5-1
  monkey 0.9.3-1ubuntu1
  mini-httpd 1.19-9.2build1
  micro-httpd 20051212-13
  mathopd 1.5p6-1.1
  lighttpd 1.4.28-2ubuntu2
  ebhttpd 1:1.0.dfsg.1-4.2
  dhttpd 1.02a-18
  cherokee 1.2.2-2build1
  bozohttpd 20100920-1
  boa 0.94.14rc21-3.1
  aolserver4-daemon 4.5.1-15
  aolserver4-core 4.5.1-15
You should explicitly select one to install.

E: Package 'httpd' has no installation candidate
root@# service apache2 start
 * Starting web server apache2                                                  apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
(98)Address already in use: make_sock: could not bind to address 0.0.0.0:80
no listening sockets available, shutting down
Unable to open logs
Action 'start' failed.
The Apache error log may have more information.
                                                                         [fail]

i want to install apache2 and php to do my project.
i was installed mysql.

thanks
prabhas

---

