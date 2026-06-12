---
title: "help with installing Ndiswrapper and source"
date: 2004-11-20
forum: Installation &amp; Upgrades
---

### Post by pezz on 2004-11-20
I am a newbie with ubuntu. I have installed Ubunutu 4.10 from a downloaded CD, 2 weeks ago.
I have Fedora 2 working with ndiswrapper and my Belkin FSD7000-card. Now I am trying to get it working with Ubuntu. I 

haven't got an internet connecting with Ubuntu because my belkin card isn't working jet [http://www.ubuntuforums.org/newthread.php?do=newthread&f=5#](http://www.ubuntuforums.org/newthread.php?do=newthread&f=5#)
Wink , so I can't use
sudo apt-get install linux-source. (correct me if I am wrong)


When trying to install ndiswrapper I get the following message:

root@ubuntu:/home/ndiswrapper-0.11 # make install
make -C driver install
make[1]: Entering directory `/home/ndiswrapper-0.11/driver'
make -C /lib/modules/2.6.8.1-3-386/build 

SUBDIRS=/home/ndiswrapper-0.11/driver \
        NDISWRAPPER_VERSION=0.11 \
        EXTRA_VERSION= modules
/usr/src/linux-headers-2.6.8.1-3-386/scripts/gcc-version.sh: line 1: gcc: command not found
/usr/src/linux-headers-2.6.8.1-3-386/scripts/gcc-version.sh: line 1: gcc: command not found
make[2]: Entering directory `/usr/src/linux-headers-2.6.8.1-3-386'
  CC [M]  /home/ndiswrapper-0.11/driver/wrapper.o
/bin/sh: line 1: gcc: command not found
make[3]: *** [/home/ndiswrapper-0.11/driver/wrapper.o] Error 127
make[2]: *** [_module_/home/ndiswrapper-0.11/driver] Error 

2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.8.1-3-386'
make[1]: *** [default] Error 2
make[1]: Leaving directory `/home/ndiswrapper-0.11/driver'
make: *** [install] Error 2


I found out that I have to install te source. So I downloaded linux-2.6.8.1.tar.gz from 

[http://archive.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.8.1/](http://archive.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.8.1/) 
I placed the file in usr/src
then 
#tar -zxvf linux-2.6.8.1.tar.gz
and made a link with
sudo ln -sf /usr/src/linux-2.6.8.1/kernel /usr/src/linux (I don't know why I should do this but read is somewhere)
When installing ndiswrapper I got the same error message (like above).


I also tried
# dpkg -i linux-image-2.6.8.1-30386_2.6.8.1-16_i386.deb
rebooted and tried to install ndiswrapper. Still got the same error message.

I have read a lot of things on the internet but stil don't know what to do. 
Can someone help me installing the source? After that I can try to install ndiswrapper.
At first, is the source (linux-2.6.8.1.tar.gz) I downloaded from [http://archive.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.8.1/](http://archive.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.8.1/) the right one? I not which one do I need?

Thanx in advance,
Pezz [http://www.ubuntuforums.org/newthread.php?do=newthread&f=5#](http://www.ubuntuforums.org/newthread.php?do=newthread&f=5#)
Confused:wink:  :wink:  :wink:  :wink:

---

### Post by emperor on 2004-11-20
You'll also need to install the GNU C Compiler (gcc) and the "linux-kernel-headers" package.

---

### Post by pezz on 2004-11-20
Allright,

installed gcc with synaptic and I can install ndiswrapper.  Okee, I will try it form there.

Thanx.

---

### Post by pezz on 2004-11-20
It works!

I am now online with Ubuntu and ndiswrapper.

Thanx again.

Pezz

---

### Post by mikeymike on 2004-11-30
i jus installed ubuntu tonight can someone tell me how to get the kernel source, GCC and whatever else i need for ndiswrapper to work.. im a noob to this distrib coming from FC3

---

### Post by strips on 2004-12-01
Quick guide:

Search for package by keyword:
```
apt-cache search "keyword"
```
*apt-cache search* can give too many hits at times. I use grep to narrow the search. If you dont know grep, Google!

Installing package:
```
apt-get install "package-name"
```

Uninstall package:
```
apt-get --purge remove "package-name"
```
The *--purge* switch makes sure all the config files are wiped. Nice to fix botched installs. If you want to keep config files drop the switch.

Regards
Stian H. Larssen

---

### Post by mikeymike on 2004-12-01
[QUOTE=strips]Quick guide:

Search for package by keyword:
```
apt-cache search "keyword"
```
*apt-cache search* can give too many hits at times. I use grep to narrow the search. If you dont know grep, Google!

Installing package:
```
apt-get install "package-name"
```

Uninstall package:
```
apt-get --purge remove "package-name"
```
The *--purge* switch makes sure all the config files are wiped. Nice to fix botched installs. If you want to keep config files drop the switch.

Regards
Stian H. Larssen[/QUOTE]
 i probably should have said i dont have a working internet connection in ubuntu... so i need the source of the packages :) cause i know how to use apt-get install 

thanks anyways

---

