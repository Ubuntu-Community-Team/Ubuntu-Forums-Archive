---
title: "Cisco VPN install for 7.10"
date: 2007-10-22
forum: Installation &amp; Upgrades
---

### Post by cybertrekman on 2007-10-22
Hi, Firstly I totally new at this linux thing having purchased a Lenovo T60, thrown away Vista and loaded Ubuntu 7.10 last week. 

Got over some issues with synching to my Palm TX with Evolution (eventually) but now I need to install Cisco VPN for remote access to work.

Dowloaded file from Cisco site, got a VPN folder create with the unzipped Cisco files and ran install pretty much according to: 

[http://www.longren.org/2007/05/17/how-to-cisco-vpn-client-on-ubuntu-704-feisty-fawn/](http://www.longren.org/2007/05/17/how-to-cisco-vpn-client-on-ubuntu-704-feisty-fawn/)

This is the result:

Cisco Systems VPN Client Version 4.8.00 (0490) Linux Installer
Copyright (C) 1998-2005 Cisco Systems, Inc. All Rights Reserved.

By installing this product you agree that you have read the
license.txt file (The VPN Client license) and will comply with
its terms. 


Directory where binaries will be installed [/usr/local/bin]/etc/opt/cisco-vpnclient/profiles/

Directory "/etc/opt/cisco-vpnclient/profiles/" doesn't exist. Create ? [y]y

Automatically start the VPN service at boot time [yes]n

In order to build the VPN kernel module, you must have the
kernel headers for the version of the kernel you are running.


Directory containing linux kernel source code [/lib/modules/2.6.22-14-generic/build]

* Binaries will be installed in "/etc/opt/cisco-vpnclient/profiles/".
* Modules will be installed in "/lib/modules/2.6.22-14-generic/CiscoVPN".
* The VPN service will *NOT* be started automatically at boot time.
* Kernel source from "/lib/modules/2.6.22-14-generic/build" will be used to build the module.

Is the above correct [y]y

Create directory "/etc/opt/cisco-vpnclient/profiles/".
Making module
make -C /lib/modules/2.6.22-14-generic/build SUBDIRS=/home/alexander/vpnclient modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.22-14-generic'
  CC [M]  /home/alexander/vpnclient/linuxcniapi.o
/home/alexander/vpnclient/linuxcniapi.c:12:26: error: linux/config.h: No such file or directory
/home/alexander/vpnclient/linuxcniapi.c: In function ‘CniInjectReceive’:
/home/alexander/vpnclient/linuxcniapi.c:297: warning: implicit declaration of function ‘skb_set_timestamp’
/home/alexander/vpnclient/linuxcniapi.c:331: error: ‘struct sk_buff’ has no member named ‘nh’
/home/alexander/vpnclient/linuxcniapi.c:332: error: ‘struct sk_buff’ has no member named ‘mac’
/home/alexander/vpnclient/linuxcniapi.c: In function ‘CniInjectSend’:
/home/alexander/vpnclient/linuxcniapi.c:454: error: ‘struct sk_buff’ has no member named ‘mac’
/home/alexander/vpnclient/linuxcniapi.c:455: error: ‘struct sk_buff’ has no member named ‘nh’
/home/alexander/vpnclient/linuxcniapi.c:458: error: ‘struct sk_buff’ has no member named ‘h’
/home/alexander/vpnclient/linuxcniapi.c:458: error: ‘struct sk_buff’ has no member named ‘nh’
make[2]: *** [/home/alexander/vpnclient/linuxcniapi.o] Error 1
make[1]: *** [_module_/home/alexander/vpnclient] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'
make: *** [default] Error 2
Failed to make module "cisco_ipsec.ko".
alexander@alexander-T60:~/vpnclient$ 

Seems to indicate it didn´t work. Any idea´s what I need to do now - in very simple language for a ubuntu dummy:confused:

---

### Post by andraycho on 2007-10-22
You need to you version 4.8.01.0640. See [http://ubuntuforums.org/showthread.php?t=581217]("http://ubuntuforums.org/showthread.php?t=581217")

---

### Post by cybertrekman on 2007-10-23
Thanks for the redirection to the other thread, install is OK now, just dont know how to configure it now and to enable launch from a desktop icon. I have raised this on the other thread.

---

