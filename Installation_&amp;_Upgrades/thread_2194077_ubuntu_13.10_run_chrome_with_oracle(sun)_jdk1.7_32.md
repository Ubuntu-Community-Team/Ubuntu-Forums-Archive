---
title: "ubuntu 13.10 run chrome with oracle(sun) jdk1.7 32 bit and not 64 bit"
date: 2013-12-16
forum: Installation &amp; Upgrades
---

### Post by tomerbd on 2013-12-16
I have 13.10 64 bit ubuntu, I have (manually downloaded and extracted) both jdk 1.7 32 and 64 bit in two folders.

I want chrome to run applets with jdk1.7 32 bit unfortunately it keeps asking me to install java plugin when i access a test page such as:

[http://www.java.com/en/download/installed.jsp?detect=jre](http://www.java.com/en/download/installed.jsp?detect=jre)
the way I point to jdk 1.7 32 bit is as following:

> /opt/google/chrome/plugins/libnpjp2.so -> /home/myuser/dev/jdk1.7.0-32/jre/lib/i386/libnpjp2.so

note when i run this java it looks fine:

> e$ /home/myuser/dev/jdk1.7.0-32/bin/java -version 
java version "1.7.0_25" Java(TM) SE Runtime Environment (build 1.7.0_25-b15) Java HotSpot(TM) Server VM (build 23.25-b01, mixed mode)

if i run chrome with 64 bit java plugin it runs applets well (does not need to install java plugin)

see:

> /opt/google/chrome/plugins/libnpjp2.so -> /home/myuser/dev/jdk1.7.0/jre/lib/amd64/libnpjp2.so

can anyone guide me through having chrome run well with jre 1.7 32 bit plugin?

question also here (feel free to reply to either I will paste the answer to the other place or you can paste reply to both place... thanks!)
[http://superuser.com/questions/689055/ubuntu-13-10-run-chrome-with-oraclesun-jdk1-7-32-bit-and-not-64-bit](http://superuser.com/questions/689055/ubuntu-13-10-run-chrome-with-oraclesun-jdk1-7-32-bit-and-not-64-bit)

thanks!

---

