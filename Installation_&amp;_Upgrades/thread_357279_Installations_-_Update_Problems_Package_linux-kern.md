---
title: "Installations - Update Problems Package linux-kernel-headers is a virtual package"
date: 2007-02-09
forum: Installation &amp; Upgrades
---

### Post by James6380 on 2007-02-09
root@mailserver:~# apt-get install binutils cpp cpp-4.0 fetchmail flex gcc gcc-4.0 libarchive-zip-perl libc6-dev libcompress-zlib-perl libdb4.3-dev libpcre3 libpopt-dev linux-kernel-headers lynx m4 make ncftp nmap openssl perl perl-modules unzip zip zlib1g-dev autoconf automake1.9 libtool bison autotools-dev g++
Reading package lists... Done
Building dependency tree
Reading state information... Done
Package linux-kernel-headers is a virtual package provided by:
  linux-libc-dev 2.6.17.1-11.35
You should explicitly select one to install.
E: Package linux-kernel-headers has no installation candidate

Help me I am following these instructions [http://www.howtoforge.com/perfect_setup_ubuntu_6.10_p4](http://www.howtoforge.com/perfect_setup_ubuntu_6.10_p4)

I keep getting this error message :( I need help

---

### Post by James6380 on 2007-02-09
root@mailserver:/# apt-get install proftpd proftpd-common ucf
Reading package lists... Done
Building dependency tree
Reading state information... Done
Package proftpd-common is a virtual package provided by:
  proftpd 1.3.0-9ubuntu0.1
You should explicitly select one to install.
E: Package proftpd-common has no installation candidate
root@mailserver:/#

following instructions from [http://www.howtoforge.com/perfect_setup_ubuntu_6.10_p6](http://www.howtoforge.com/perfect_setup_ubuntu_6.10_p6)

---

### Post by RoboRutt on 2007-03-22
Heya, 

New to Ubuntu too, but I found something that might help...

I ran the same command line - with linux-kernel-headers removed... worked fine... 

Now to work out how to instrall 'linux-kernel-headers' ... if I have to at all :)

Cheers, 
RR

---

### Post by RoboRutt on 2007-03-22
update - :)

Don't know if you have it sorted, but for those who follow, check out [http://www.ubuntuforums.org/showthread.php?t=321202&highlight=you+should+explicitly+select+one+to+install](http://www.ubuntuforums.org/showthread.php?t=321202&highlight=you+should+explicitly+select+one+to+install)

I couldn't  run the command :

apt-get -y install linux-headers-'uname -r' as suggested, but i ran them separately... so:

# uname -r (gets kernel version)
then
#apt-get -y install linux-headers-XXXXX (where XXXX is the results from the previous uname command)

Hope that helps :)

RR

---

