---
title: "nameserver not working after installing ispconfig3 in apache2"
date: 2011-05-12
forum: Installation &amp; Upgrades
---

### Post by bruce2wayne on 2011-05-12
hi, guys this is shan and i'm quite new to ubuntu and recently(i mean just hours back) i installed lamp server with ispconfig3 as per the howtoforge documentation and after installing ispconfig successfully i get the error message when i start the apache server using the 
```
/etc/init.d/apache2 start
```the error message is as follows:

```
* Starting web server apache2                                                                                                                                          apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
[Fri May 13 03:41:20 2011] [warn] NameVirtualHost 127.0.0.12:80 has no VirtualHosts
[Fri May 13 03:41:20 2011] [warn] NameVirtualHost 127.0.0.12:443 has no VirtualHosts
                                                                                                                                                                 [ OK ]

```and when i try to use the name in browser it either shows an error message that firefox couldn't find the server or goes to another domain, but when i type localhost it works fine, and when i typed the command 

```
root@shan-lap:/etc/apache2/sites-enabled# apache2 -t
apache2: bad user name ${APACHE_RUN_USER}

```and i did search around available solutions in the forum but it was of no help, so, please help me to work on this problem.

thanks in advance:P

---

