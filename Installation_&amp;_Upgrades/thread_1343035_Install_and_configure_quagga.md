---
title: "Install and configure quagga"
date: 2009-12-01
forum: Installation &amp; Upgrades
---

### Post by ivboy on 2009-12-01
Hi
I'm new with quagga, and i need a simple way to install and compile. So here is the problem ... i downloaded quagga from [http://www.quagga.net/](http://www.quagga.net/)ver [0.98.6  ]("http://www.quagga.net/download/quagga-0.98.6.tar.gz")i extract the tar.gz file and in terminal i did ./configure .. it seems ok the out put was
[IMG]http://img231.imageshack.us/img231/8206/configure.jpg[/IMG]
 ... next i do make and the error was ... 
[IMG]http://img4.imageshack.us/img4/2500/makeo.jpg[/IMG]

> gcc -DHAVE_CONFIG_H -DSYSCONFDIR=\"/usr/local/etc/\" -I. -I. -I.. -I.. -I.. -I../lib -Os -g -Wall -Wsign-compare -Wpointer-arith -Wbad-function-cast -Wwrite-strings -MT sockopt.lo -MD -MP -MF .deps/sockopt.Tpo -c sockopt.c  -fPIC -DPIC -o .libs/sockopt.o
sockopt.c: In function 'getsockopt_ipv6_ifindex':
sockopt.c:150: error: dereferencing pointer to incomplete type
make[2]: *** [sockopt.lo] Error 1
make[2]: Leaving directory `/home/student/Desktop/quagga-0.98.6/lib'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/student/Desktop/quagga-0.98.6'
make: *** [all] Error 2So can pls someone help me and explain where am i doing wrong... and if i change something in config file or any file, this changes i'm going to make in the extracted files where i do this or in installed files ... 
i would like to test some things but i'm a beginner :) in quagga :) ... 

Excuse me for my poor english ! :)
and
Thanks in advanced!

---

### Post by oldos2er on 2009-12-01
quagga_0.99.13-1 is in the repositories (for 9.10); is there some particular reason you need to compile an older version?

---

### Post by ivboy on 2009-12-01
Well there is [http://www.quagga.net/download.php](http://www.quagga.net/download.php) 0.98.6 stable version and 0.99.15 unstable ... but i have no reason for using that version ... any version that is stable is ok for me to used . just to pass the configure, make and make install .... this error is annoying :)

---

### Post by ivboy on 2009-12-03
I guess you were right, you gave me an idea ... i use Synaptic and i download and install that version quagga_0.99.9-6 i pass the ./configure :) and i think i pass make, and make install ... i'm just a little confuse about the out put of make and make install ... " Nothing to be done for 'all' " im guessing everything is ok ... 
[[IMG]http://img697.imageshack.us/img697/4356/make.png[/IMG]]("http://img697.imageshack.us/img697/4356/make.png")

[[IMG]http://img301.imageshack.us/img301/4033/makeinstall.png[/IMG]]("http://img301.imageshack.us/img301/4033/makeinstall.png")

anyway where can i change the behavior of the RIPng in quagga, and then i would like to see if it can pass the compiling test;) ... tnx again for reply 

Excuse me for my poor english ! :)

Thanks in advanced!

---

### Post by rachael4u on 2009-12-03
thnxxxxx for sharing...

---

### Post by ivboy on 2009-12-05
np :popcorn:
So any idea what to do now whit this errors ....

---

### Post by ivboy on 2010-01-22
OK so this is final ... after the compiling and installing i have a problem with starting the daemons of the quagga ... so i found the solution and i would like to share with all off you ...

Before configuring and compiling the quagga i installed all dependency(package) i needed for quagga .. "**apt-get build-dep quagga**" ...

so when you compile the quagga you have to give the path for all configurations files and libraries used by quagga for starting ... i use this one **/opt/quagga** .... and this is done by this comand: **./confiure –prefix=/opt/quagga –localstatedir=/opt/quagga sysconfdir=/opt/quagga **
and you create new folder: **mkdir /opt/quagga**
afther this u add new user : **adduser quagga **

and you give the privilegde for the user quagga over the folder: **/opt/quagga** and for the folders and subfolders you give the privilegde  for all rights : **reading, changing and executing**
**chown quagga: quagga /opt/quagga **and** chmod 777 /opt/quagga **

then you use **make** and **make install **
that's it .. for starting the zebra daemon you use this comand **/opt/quagga/sbin/zebra &**
to see if this daemon is started you use the **netstat -a |grep zebra**  or **netstat -a |grep 2601 **
to get in to the **zebra** you use **telnet localhost 2601** or **telnet localhost zebra**

Hope it will work for u !
Have fun !

---

### Post by smartgost on 2011-03-11
i am having problem with doing telnet localhost ospfd and similar protocol deamons.....any one has an idea where i m going worng

---

### Post by lilium110 on 2011-07-06
Hi,
i'm trying to install & configure quagga in OpenSuse 10.2(I know it's ubuntu forum but i need help quickly:?)
when i type **./configure** cmd i get this error :
**"invalid value of canonical build"**:confused:
I don't know the reason:frown: would anyone plz help me??

---

