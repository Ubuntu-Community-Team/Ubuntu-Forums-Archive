---
title: "install on software raid - missing md's"
date: 2012-03-14
forum: Installation &amp; Upgrades
---

### Post by aetienne on 2012-03-14
Trying to do an install of ubuntu-12.04-beta1-alternate-amd64.iso on a Dell T110. I was trying to get the root partition on software raid 1. First time around everything seemed to go okay. Just like the guides indicated. However the system would never get past the ubuntu screen with the red dots. I left it over night. Got feed up and rebooted, same thing. Installed alternate from USB drive again, only this time none of the software raid devices will ever show up as mount points under the partition utility. It looks like you are creatign them, they just never show up and there are none to delete. So I think they are not getting created. I have tried repartitioning several time. Any idea what is wrong?
 
Maybe I am going about things the wrong way. Here is what I want in the end:
 
Entire system on sofware raid. All system partitions (/, /usr, /var, etc) on raid 1 and data (/export) on raid 5. I have four 1TB drives.
 
Thanks in advance,
Al

---

### Post by aetienne on 2012-03-14
Apparently this is what happened.  First go around on the install, the window manager didn't get installed and the console was redirected to the remote management function of the Dell, so everything was probably okay; I just didn't get any response on the monitor and didn't try to ssh to the machine.
 
I was finally able to create the software raid during install after partioning and formating the disk with a working non-raid install on the same machine.
 
Window manager still didn't install this time around either....

---

