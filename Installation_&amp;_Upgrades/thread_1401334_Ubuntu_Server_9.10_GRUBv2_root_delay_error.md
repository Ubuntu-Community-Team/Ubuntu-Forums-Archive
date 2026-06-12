---
title: "Ubuntu Server 9.10 GRUBv2 root delay error"
date: 2010-02-07
forum: Installation &amp; Upgrades
---

### Post by baraka2000 on 2010-02-07
Hey Ubuntu peeps,

I'm a novice. Any help is appreciated.

I'm attempting to install Ubuntu server 9.1 on a Dell PowerEdge server. I have a mirror hardware RAID for the system drive (2 SAS drives RAID level 1). Installation went smoothly, but it did not boot smoothly. I got this error:



Starting up...
Loading, please wait...
Gave up waiting for root device.  Common problems:
 -Boot args (cat /proc/cmdline)
   -Check root delay = (did the system wait long enough?)
   -Check root=(did the system wait for the right device?)
 -Missing modules (cat /proc/modules; ls /dev)

I found lots of fixes online, basically changing the root delay to 35 or longer. Like this:

[http://stoilis.wordpress.com/2009/11/20/error-on-first-boot-after-installing-ubuntu-on-a-dell-r410/](http://stoilis.wordpress.com/2009/11/20/error-on-first-boot-after-installing-ubuntu-on-a-dell-r410/)

Problem is all these fixes involve changing a line in the file /boot/grub/menu.lst

This file doesn't exist on the current version of GRUB (v2). The file that replaced this menu.lst in the new GRUB isnt supposed to be edited by the user. But only changed with updates. And yes I did try running the system updates and grub update, neither worked.

So my server works, just doesn't boot clean. 

Please help us Obi-wan.

---

### Post by Blindbatts on 2010-02-24
I'm having this exact same problem on my r410 server.


In 9.04, I was able to add rootdelay=35 to the /boot/grub/menu.lst


I can get the system to boot successfully if I hold shift during boot, and edit the grub line to add rootdelay=35, however I'm not sure how to make this stick with the new grub2 in 9.10.

FWIW this started happening after upgrading from 9.04 to 9.10, I forgot about my rootdelay=35 workaround from when I initially setup the server, so I backed up my files and clean installed, same issue from a clean install.



I performed a sudo update-grub after booting the system, along with doing an apt-get update/upgrade.


The new grub2 configuration seems very confusing to me, or maybe I'm just used to the old way with menu.lst.

I looked into editing the /boot/grub/grub.cfg file but it has lots of warnings about how it shouldn't be edited manually and any changes will be lost when an update is applied, argh.

---

### Post by -)RaDaR(- on 2010-03-04
Edit */etc/default/grub*

add *rootdelay=xx* to this line:
GRUB_CMDLINE_LINUX_DEFAULT="**rootdelay=60** quiet splash"

then exec: sudo *update-grub*

---

