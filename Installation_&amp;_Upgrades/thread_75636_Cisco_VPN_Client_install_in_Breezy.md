---
title: "Cisco VPN Client install in Breezy"
date: 2005-10-14
forum: Installation &amp; Upgrades
---

### Post by haiku on 2005-10-14
Has anyone gotten this to work with breezy?  The installation script is not able to build the module on my install.

My kernel version is: 2.6.12-9-386

I have tried all of the following from stuff i've read in other threads:

Made sure I have various versions of Gcc 3.3, 3.4, etc
Downloaded the kernel source: linux-source-2.6.12
Downloaded the kernel headers: linux-headers-2.6.12-9


I can't really post the log because it scrolls about a thousand lines of warnings and errors when tryin gto compile, but here's the first portion of it:
```

...
Directory containing linux kernel source code [/usr/src/linux]

* Binaries will be installed in "/usr/local/bin".
* Modules will be installed in "/lib/modules/2.6.12-9-386/CiscoVPN".
* The VPN service will be started AUTOMATICALLY at boot time.
* Kernel source from "/usr/src/linux" will be used to build the module.

Is the above correct [y]

Making module
make -C /usr/src/linux SUBDIRS=/home/jrapp/Desktop/Linux/vpnclient modules
make[1]: Entering directory `/usr/src/linux-source-2.6.12'
Makefile:485: .config: No such file or directory

  WARNING: Symbol version dump /usr/src/linux-source-2.6.12/Module.symvers
           is missing; modules will have no dependencies and modversions.

  CC [M]  /home/jrapp/Desktop/Linux/vpnclient/linuxcniapi.o
In file included from /home/jrapp/Desktop/Linux/vpnclient/linuxcniapi.c:12:
include/linux/config.h:4:28: linux/autoconf.h: No such file or directory
/home/jrapp/Desktop/Linux/vpnclient/linuxcniapi.c:13:27: linux/version.h: No suc h file or directory
In file included from include/linux/posix_types.h:47,
                 from include/linux/types.h:13,
                 from include/linux/if.h:22,
                 from include/linux/netdevice.h:28,
                 from /home/jrapp/Desktop/Linux/vpnclient/linuxcniapi.c:14:
/usr/lib/gcc/i486-linux-gnu/3.4.5/include/asm/posix_types.h:13:22: features.h: N o such file or directory
/usr/lib/gcc/i486-linux-gnu/3.4.5/include/asm/posix_types.h:14:35: no include pa th in which to search for asm/posix_types.h
In file included from include/linux/if.h:22,
                 from include/linux/netdevice.h:28,
                 from /home/jrapp/Desktop/Linux/vpnclient/linuxcniapi.c:14:
include/linux/types.h:14:23: asm/types.h: No such file or directory
In file included from include/linux/if.h:22,
                 from include/linux/netdevice.h:28,
                 from /home/jrapp/Desktop/Linux/vpnclient/linuxcniapi.c:14:
include/linux/types.h:18: error: parse error before "__kernel_dev_t"
include/linux/types.h:18: warning: type defaults to `int' in declaration of `__k ernel_dev_t'
include/linux/types.h:18: warning: data definition has no type or storage class
include/linux/types.h:21: error: parse error before "dev_t"
include/linux/types.h:21: warning: type defaults to `int' in declaration of `dev _t'
include/linux/types.h:21: warning: data definition has no type or storage class
include/linux/types.h:22: error: parse error before "ino_t"
include/linux/types.h:22: warning: type defaults to `int' in declaration of `ino _t'
include/linux/types.h:22: warning: data definition has no type or storage class
include/linux/types.h:23: error: parse error before "mode_t"
include/linux/types.h:23: warning: type defaults to `int' in declaration of `mod e_t'
include/linux/types.h:23: warning: data definition has no type or storage class
include/linux/types.h:24: error: parse error before "nlink_t"
include/linux/types.h:24: warning: type defaults to `int' in declaration of `nli nk_t'

```

I would greatly appreciate any insight.

thanks!

---

### Post by shenki on 2005-10-14
I'm not too sure about your comiliation errors (do you have a symlink /usr/src/linux that points to /usr/src/linux-2.6.XXXXXX?), but after wrestling with the cisco vpn client for linux myself a few times, I went with the open source vpnc - performs the same function, with a lot less hastle.

simply [FONT="Lucida Console"]apt-get install vpnc[/FONT]

you can make a config file as outlined in [FONT="Lucida Console"]man vpnc[/FONT], and hence type [FONT="Lucida Console"]vpnc-connect *location*'[/FONT] - keeps things nice and simple, much easier than that horrible cisco client, imo.

---

### Post by haiku on 2005-10-14
[QUOTE=shenki]I'm not too sure about your comiliation errors (do you have a symlink /usr/src/linux that points to /usr/src/linux-2.6.XXXXXX?), but after wrestling with the cisco vpn client for linux myself a few times, I went with the open source vpnc - performs the same function, with a lot less hastle.

simply [FONT="Lucida Console"]apt-get install vpnc[/FONT]

you can make a config file as outlined in [FONT="Lucida Console"]man vpnc[/FONT], and hence type [FONT="Lucida Console"]vpnc-connect *location*'[/FONT] - keeps things nice and simple, much easier than that horrible cisco client, imo.[/QUOTE]

I'm not really that familiar with vpn. I need to use a client to access the wireless on my college campus.  I installed vpnc earlier this evening but wasn't sure how to set it up based on the big/ugly profile i'm supposed to use with the cisco client.

and, yes I do have a symlink at /usr/src/linux pointing to my source directory, i've also tried pointing that symlink to the headers directory which seemed to result in an even more serious error.

---

### Post by shenki on 2005-10-14
Here is a quick guide on how I translated my Cisco config file, located in /etc/CiscoSystemsVPNClient/Profiles, and has the extention .pcf (also, intrestingly, if you have set up the Cisco client on windows, this is the exact same config file, just do a search for *.pcf). The names in italics are the settings from the Cisco client.

Create the file /etc/vpnc/college.conf

IPSec gateway  *Host*
IPSec ID           *GroupName*
IPSec secret     *GroupPwd*
Xauth username *UserPassword*

then type 'sudo vpnc-connect college'. It will ask for your password, and then, fingers crossed, it should connect. (a note: when you apt installed vpnc, did it install resolvconf? if not, 'sudo apt-get install resolvconf' and try again)

This is all from memory from a few months ago when I set up my own laptop to connect to my uni vpn, so I may have missed something vitally important.

If you want any help setting up the config, let me know - maybe you could PM me the cisco config file (make sure you ***** out the passwords, just in case something bad happens to the file).

---

### Post by mrsad on 2005-10-14
you must have gcc 3.4 installed and use at least the cisco vpn client 4.7.x, that worked for me.

---

### Post by haiku on 2005-10-14
Hello, thank you for all the help.

Turns out i didn't have EXACTLY the correct kernel headers, I was having trouble finding them through synaptic, but this time i just used

sudo apt-get install linux-headers-the exact version string i got from uname -r

then all I had to do was download the patched version of interceptor.c i saw in another thread and the installation worked.

---

### Post by usererror on 2006-12-16
I can't figure out what i'm missing here.

I got the Cisco VPN installed no problem, copied my pcf file from windows but i'm getting an error from my work's VPN concentrator saying my connection was dropped by the peer for "firewall policy mismatch"

I've got these ports open on my firewall at home:

# The CISCO documentation mentions several other ports, quoting:

    * UDP port 500
    * UDP port 10000 and 500 (or any other port number being used for IPSec/UDP)
    * IP protocol 50 (ESP)
    * NAT-T port 4500 UDP

but it still wont connect me.  i read something about iptables on my linux box???  

any help would be appreciated :D

---

### Post by sigrney on 2007-04-25
i have tried with no success to build the cisco module on 7.04, also vpnc sort of works for me - it connects then drops within a minute, not sure why, any help is appreciated! i installed build-essential and the kernel headers as directed from another post

tommy@tommy-laptop:~/ciscovpn/vpnclient$ sudo apt-get install build-essential
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  dpkg-dev g++ g++-4.1 libc6-dev libstdc++6-4.1-dev linux-libc-dev
Suggested packages:
  debian-keyring gcc-4.1-doc lib64stdc++6 glibc-doc manpages-dev
  libstdc++6-4.1-doc
The following NEW packages will be installed:
  build-essential dpkg-dev g++ g++-4.1 libc6-dev libstdc++6-4.1-dev
  linux-libc-dev
0 upgraded, 7 newly installed, 0 to remove and 0 not upgraded.
Need to get 8050kB of archives.
After unpacking 33.7MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main linux-libc-dev 2.6.20-15.27 [664kB]
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main libc6-dev 2.5-0ubuntu14 [3018kB]
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main libstdc++6-4.1-dev 4.1.2-0ubuntu4 [1632kB]
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main g++-4.1 4.1.2-0ubuntu4 [2581kB] 
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main g++ 4:4.1.2-1ubuntu1 [1428B]    
Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main dpkg-dev 1.13.24ubuntu6 [147kB] 
Get:7 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main build-essential 11.3 [6974B]    
Fetched 8050kB in 27s (288kB/s)                                                
Selecting previously deselected package linux-libc-dev.
(Reading database ... 100428 files and directories currently installed.)
Unpacking linux-libc-dev (from .../linux-libc-dev_2.6.20-15.27_i386.deb) ...
Selecting previously deselected package libc6-dev.
Unpacking libc6-dev (from .../libc6-dev_2.5-0ubuntu14_i386.deb) ...
Selecting previously deselected package libstdc++6-4.1-dev.
Unpacking libstdc++6-4.1-dev (from .../libstdc++6-4.1-dev_4.1.2-0ubuntu4_i386.deb) ...
Selecting previously deselected package g++-4.1.
Unpacking g++-4.1 (from .../g++-4.1_4.1.2-0ubuntu4_i386.deb) ...
Selecting previously deselected package g++.
Unpacking g++ (from .../g++_4%3a4.1.2-1ubuntu1_i386.deb) ...
Selecting previously deselected package dpkg-dev.
Unpacking dpkg-dev (from .../dpkg-dev_1.13.24ubuntu6_all.deb) ...
Selecting previously deselected package build-essential.
Unpacking build-essential (from .../build-essential_11.3_i386.deb) ...
Setting up linux-libc-dev (2.6.20-15.27) ...
Setting up libc6-dev (2.5-0ubuntu14) ...
Setting up dpkg-dev (1.13.24ubuntu6) ...
Setting up libstdc++6-4.1-dev (4.1.2-0ubuntu4) ...
Setting up g++-4.1 (4.1.2-0ubuntu4) ...
Setting up g++ (4.1.2-1ubuntu1) ...

Setting up build-essential (11.3) ...
tommy@tommy-laptop:~/ciscovpn/vpnclient$ uname -r
2.6.20-15-generic
tommy@tommy-laptop:~/ciscovpn/vpnclient$ sudo apt-get install linux-headers-2.6.20-15-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-headers-2.6.20-15-generic is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
tommy@tommy-laptop:~/ciscovpn/vpnclient$ make
make -C /lib/modules/2.6.20-15-generic/build SUBDIRS=/home/tommy/ciscovpn/vpnclient modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-15-generic'
  CC [M]  /home/tommy/ciscovpn/vpnclient/linuxcniapi.o
/home/tommy/ciscovpn/vpnclient/linuxcniapi.c:12:26: error: linux/config.h: No such file or directory
/home/tommy/ciscovpn/vpnclient/linuxcniapi.c: In function ‘CniInjectReceive’:
/home/tommy/ciscovpn/vpnclient/linuxcniapi.c:279: warning: unused variable ‘timecount’
/home/tommy/ciscovpn/vpnclient/linuxcniapi.c: In function ‘CniInjectSend’:
/home/tommy/ciscovpn/vpnclient/linuxcniapi.c:403: warning: unused variable ‘timecount’
/home/tommy/ciscovpn/vpnclient/linuxcniapi.c: At top level:
/home/tommy/ciscovpn/vpnclient/linuxcniapi.c:557: fatal error: opening dependency file /home/tommy/ciscovpn/vpnclient/.linuxcniapi.o.d: Permission denied
compilation terminated.
make[2]: *** [/home/tommy/ciscovpn/vpnclient/linuxcniapi.o] Error 1
make[1]: *** [_module_/home/tommy/ciscovpn/vpnclient] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-15-generic'
make: *** [default] Error 2
tommy@tommy-laptop:~/ciscovpn/vpnclient$ sudo make
make -C /lib/modules/2.6.20-15-generic/build SUBDIRS=/home/tommy/ciscovpn/vpnclient modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-15-generic'
  CC [M]  /home/tommy/ciscovpn/vpnclient/linuxcniapi.o
/home/tommy/ciscovpn/vpnclient/linuxcniapi.c:12:26: error: linux/config.h: No such file or directory
/home/tommy/ciscovpn/vpnclient/linuxcniapi.c: In function ‘CniInjectReceive’:
/home/tommy/ciscovpn/vpnclient/linuxcniapi.c:279: warning: unused variable ‘timecount’
/home/tommy/ciscovpn/vpnclient/linuxcniapi.c: In function ‘CniInjectSend’:
/home/tommy/ciscovpn/vpnclient/linuxcniapi.c:403: warning: unused variable ‘timecount’
make[2]: *** [/home/tommy/ciscovpn/vpnclient/linuxcniapi.o] Error 1
make[1]: *** [_module_/home/tommy/ciscovpn/vpnclient] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-15-generic'
make: *** [default] Error 2


tommy@tommy-laptop:~/ciscovpn/vpnclient$ sudo ./vpn_install 
Cisco Systems VPN Client Version 4.8.00 (0490) Linux Installer
Copyright (C) 1998-2005 Cisco Systems, Inc. All Rights Reserved.

By installing this product you agree that you have read the
license.txt file (The VPN Client license) and will comply with
its terms. 


Directory where binaries will be installed [/usr/local/bin]

Automatically start the VPN service at boot time [yes]

In order to build the VPN kernel module, you must have the
kernel headers for the version of the kernel you are running.


Directory containing linux kernel source code [/lib/modules/2.6.20-15-generic/build]

* Binaries will be installed in "/usr/local/bin".
* Modules will be installed in "/lib/modules/2.6.20-15-generic/CiscoVPN".
* The VPN service will be started AUTOMATICALLY at boot time.
* Kernel source from "/lib/modules/2.6.20-15-generic/build" will be used to build the module.

Is the above correct [y]

Making module
make -C /lib/modules/2.6.20-15-generic/build SUBDIRS=/home/tommy/ciscovpn/vpnclient modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-15-generic'
  CC [M]  /home/tommy/ciscovpn/vpnclient/linuxcniapi.o
/home/tommy/ciscovpn/vpnclient/linuxcniapi.c:12:26: error: linux/config.h: No such file or directory
/home/tommy/ciscovpn/vpnclient/linuxcniapi.c: In function ‘CniInjectReceive’:
/home/tommy/ciscovpn/vpnclient/linuxcniapi.c:279: warning: unused variable ‘timecount’
/home/tommy/ciscovpn/vpnclient/linuxcniapi.c: In function ‘CniInjectSend’:
/home/tommy/ciscovpn/vpnclient/linuxcniapi.c:403: warning: unused variable ‘timecount’
make[2]: *** [/home/tommy/ciscovpn/vpnclient/linuxcniapi.o] Error 1
make[1]: *** [_module_/home/tommy/ciscovpn/vpnclient] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-15-generic'
make: *** [default] Error 2
Failed to make module "cisco_ipsec.ko".
tommy@tommy-laptop:~/ciscovpn/vpnclient$

---

