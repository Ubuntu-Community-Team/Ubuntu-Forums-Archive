---
title: "Tomcat6 installation in ubuntu"
date: 2013-02-26
forum: Installation &amp; Upgrades
---

### Post by smidhunrajj on 2013-02-26
tomcat server not running properly

midhun@midhun-desktop:~$ uname -a
Linux midhun-desktop 2.6.32-38-generic #83-Ubuntu SMP Wed Jan 4 11:13:04 UTC 2012 i686 GNU/Linux
--------------------------------------------------------------
midhun@midhun-desktop:~$ sudo service tomcat6 start
[sudo] password for midhun: 
 * Starting Tomcat servlet engine tomcat6                                [fail] 
------------------------------------------------------------

---

### Post by Toz on 2013-02-26
Hello and welcome to the forums.

What does the log file say? (/var/log/tomcat6/catalina.out)

---

### Post by smidhunrajj on 2013-02-26
i created a init.d/config file using as root user and the problem was resolved .. 
any way thanks Toz for your turn up..

[http://orkus.wordpress.com/2010/08/31/howto-install-tomcat-7-on-debian-lenny/]("http://orkus.wordpress.com/2010/08/31/howto-install-tomcat-7-on-debian-lenny/")

---

