---
title: "Problems configuring kernel"
date: 2009-10-12
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by filologen on 2009-10-12
Today when I tried to update a friends Thinkpad T500 (Karmic Koala, 64 bit, all updates applied) I ran into some problems configuring the latest kernel. 

I first tried to do an update using synaptics, but then tried to do a "sudo apt-get update" and "sudo apt-get upgrade" from the command line, but got the same message. If I do a "sudo dpkg --configure -a" this is the result:

```
Setting up linux-headers-2.6.31-13-generic (2.6.31-13.44) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing linux-headers-2.6.31-13-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up linux-image-2.6.31-13-generic (2.6.31-13.44) ...
Running depmod.
WARNING: Couldn't find symtab and strtab in module /lib/modules/2.6.31-13-generic/kernel/fs/cifs/cifs.ko
WARNING: Couldn't find symtab and strtab in module /lib/modules/2.6.31-13-generic/kernel/fs/udf/udf.ko
WARNING: Couldn't find symtab and strtab in module /lib/modules/2.6.31-13-generic/kernel/drivers/video/aty/radeonfb.ko
WARNING: Couldn't find symtab and strtab in module /lib/modules/2.6.31-13-generic/kernel/drivers/char/synclink.ko
WARNING: Couldn't find symtab and strtab in module /lib/modules/2.6.31-13-generic/kernel/drivers/net/wireless/ipw2x00/ipw2200.ko
WARNING: Couldn't find symtab and strtab in module /lib/modules/2.6.31-13-generic/kernel/drivers/staging/rt2860/rt2860sta.ko
WARNING: Couldn't find symtab and strtab in module /lib/modules/2.6.31-13-generic/kernel/drivers/infiniband/hw/mthca/ib_mthca.ko
Failed to run depmod
dpkg: error processing linux-image-2.6.31-13-generic (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of linux-headers-generic:
 linux-headers-generic depends on linux-headers-2.6.31-13-generic; however:
  Package linux-headers-2.6.31-13-generic is not configured yet.
dpkg: error processing linux-headers-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.31-13-generic; however:
  Package linux-image-2.6.31-13-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 2.6.31.13.24); however:
  Package linux-image-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-headers-2.6.31-13-generic
 linux-image-2.6.31-13-generic
 linux-headers-generic
 linux-image-generic
 linux-generic

```


Any idea how to solve this?

PS: The laptop can still boot using linux-image-2.6.31-12-generic

Best regards

---

### Post by dino99 on 2009-10-12
try this:

boot on 31-12, then remove / purge 31-13 if image or header are installed or broken.

clean autoclean autoremove your cache

then, sudo aptitude install -f

look at .xsession-errors & logs (maybe you can find some reasons about this problem)

update safe-upgrade

try again to install 31-13

---

### Post by filologen on 2009-10-12
Thanks, I'll try this tonight (Danish time, it's morning here) to see if it solves the problem. 

Thanks for taking the time to answer me!

---

### Post by FirstByté on 2009-10-14
I'm not sure if my problem is generic with Filologen, but I posted my kernel issues **[ >> here <<]("http://art.ubuntuforums.org/showpost.php?p=8101407&postcount=52")** but no response or answers.

I don't wanna be posting all the details again. A synopsis of my problem is: I have graphics issues after a recent update of 'xserver-xorg-video-intel <2.9.0>' and to fix it I had to switch to Karmic Koala's kernel 2.6.31 because the kernel 2.6.30 instructed was not found [[http://archive.ubuntu.com/ubuntu/pool/main/l/linux/]](http://archive.ubuntu.com/ubuntu/pool/main/l/linux/]), only the kernel 2.6.31 was there so I installed. 

However, **I need to compile 'wl' so I can use my Broadcom 4312 onboard card again but I have issues installing the 'linux-headers-2.6.31-13-generic'** so I can't compile the **wl** let alone testing it's operability. 

All I use now is just LAN :confused:

Details (of attempts and efforts) here [URL="http://art.ubuntuforums.org/showpost.php?p=8101407&postcount=52"]

Thanks ahead

---

