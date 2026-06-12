---
title: "install ekiga (except ekiga 3.3.2-0ubuntu3) on Ubuntu 12.04"
date: 2013-03-31
forum: Installation &amp; Upgrades
---

### Post by survey1 on 2013-03-31
Hi

I searched on google and ubuntu form but unfortunately could't find the answer.
 installed ekiga 3.3.2-0ubuntu3 on Ubuntu 12.04 previously and it use to get crashed. I tried debugging using gdb but not much succes so decided to install the latest verison.

did apt-get update
and then 


root@host:/home/user1# apt-get install -s ekiga
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  libboost-signals1.46.1 libcapi20-3 libodbc1 libopal3.10.2 libpt2.10.2 odbcinst odbcinst1debian2 unixodbc
Suggested packages:
  siproxd gnugk mediaproxy ser rtpproxy asterisk yate libmyodbc odbc-postgresql tdsodbc unixodbc-bin
The following NEW packages will be installed
  ekiga libboost-signals1.46.1 libcapi20-3 libodbc1 libopal3.10.2 libpt2.10.2 odbcinst odbcinst1debian2 unixodbc
0 upgraded, 9 newly installed, 0 to remove and 42 not upgraded.
Inst libodbc1 (2.2.14p2-5ubuntu3 Ubuntu:12.04/precise [i386])
Inst odbcinst (2.2.14p2-5ubuntu3 Ubuntu:12.04/precise [i386]) []
Inst odbcinst1debian2 (2.2.14p2-5ubuntu3 Ubuntu:12.04/precise [i386])
Inst libcapi20-3 (1:3.12.20071127-0ubuntu11 Ubuntu:12.04/precise [i386])
Inst libboost-signals1.46.1 (1.46.1-7ubuntu3 Ubuntu:12.04/precise [i386])
Inst unixodbc (2.2.14p2-5ubuntu3 Ubuntu:12.04/precise [i386])
Inst libpt2.10.2 (2.10.2~dfsg-0ubuntu1 Ubuntu:12.04/precise [i386])
Inst libopal3.10.2 (3.10.2~dfsg-0ubuntu1 Ubuntu:12.04/precise [i386])
Inst ekiga (3.3.2-0ubuntu3 Ubuntu:12.04/precise [i386])
Conf libodbc1 (2.2.14p2-5ubuntu3 Ubuntu:12.04/precise [i386])
Conf odbcinst (2.2.14p2-5ubuntu3 Ubuntu:12.04/precise [i386])
Conf odbcinst1debian2 (2.2.14p2-5ubuntu3 Ubuntu:12.04/precise [i386])
Conf libcapi20-3 (1:3.12.20071127-0ubuntu11 Ubuntu:12.04/precise [i386])
Conf libboost-signals1.46.1 (1.46.1-7ubuntu3 Ubuntu:12.04/precise [i386])
Conf unixodbc (2.2.14p2-5ubuntu3 Ubuntu:12.04/precise [i386])
Conf libpt2.10.2 (2.10.2~dfsg-0ubuntu1 Ubuntu:12.04/precise [i386])
Conf libopal3.10.2 (3.10.2~dfsg-0ubuntu1 Ubuntu:12.04/precise [i386])
Conf ekiga (3.3.2-0ubuntu3 Ubuntu:12.04/precise [i386])

This still wants to install 3.3.2-0ubuntu3 which I don't want. Either I want to install Ekiga versions 
4.0.1-1     or
3.3.2-0ubuntu7 
which are available at [https://launchpad.net/ubuntu/+source/ekiga](https://launchpad.net/ubuntu/+source/ekiga) 
I am unable to figure out how to install one of those. Tried installing via PPA but not much success. 

Can anyone please guide.
Thanks a lot in advance
[TABLE="class: listing"]
[TR="class: archive_package_row"]
[TD][/TD]
[TD][/TD]
[TD][/TD]
[/TR]
[TR]
[TD="colspan: 3"][/TD]
[/TR]
[TR="class: section-heading shaded"]
[TD="colspan: 3"][/TD]
[/TR]
[TR="class: archive_package_row"]
[TD][/TD]
[/TR]
[/TABLE]

---

