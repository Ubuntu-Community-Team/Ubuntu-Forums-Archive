---
title: "X server error after nvidia-glx install"
date: 2007-07-01
forum: Installation &amp; Upgrades
---

### Post by dwebb86 on 2007-07-01
hey guys,
I just got a new E1505 Dell with Ubuntu 7.04 pre-installed on it about a week ago.
Been screwing with it ever since, and I found Compiz Fusion, and couldn't get it to work for the life of me.
I screwed with my system so much, I decided to reinstall the OS and start from scratch (I didn't have anything cool on the computer yet anyways)

...so, reinstallation went fine, I'm in the middle of the 3rd one now. 
But yeah, on to the point, when I finish installing the OS, and do **sudo apt-get install nvidia-glx** or just use the restricted drivers manager for the same thing, as soon as I reboot my computer I get:
**(WW) NVIDIA: no matching device section for instance (busID PCI:1:0:0) found**
and:
**x server error: no screens found**

I've been looking through forums and trying various things, but none of them seem to work... and here I am at 58% of reinstalling Ubuntu for the 3rd time. 

Anyone know what I can do?

---

### Post by confused57 on 2007-07-01
> **dwebb86 said:**
> hey guys,
I just got a new E1505 Dell with Ubuntu 7.04 pre-installed on it about a week ago.
Been screwing with it ever since, and I found Compiz Fusion, and couldn't get it to work for the life of me.
I screwed with my system so much, I decided to reinstall the OS and start from scratch (I didn't have anything cool on the computer yet anyways)

...so, reinstallation went fine, I'm in the middle of the 3rd one now. 
But yeah, on to the point, when I finish installing the OS, and do **sudo apt-get install nvidia-glx** or just use the restricted drivers manager for the same thing, as soon as I reboot my computer I get:
**(WW) NVIDIA: no matching device section for instance (busID PCI:1:0:0) found**
and:
**x server error: no screens found**

I've been looking through forums and trying various things, but none of them seem to work... and here I am at 58% of reinstalling Ubuntu for the 3rd time. 

Anyone know what I can do?
This tutorial worked for me:
[http://ubuntuforums.org/showthread.php?t=432056&highlight=Nvidia+Feisty](http://ubuntuforums.org/showthread.php?t=432056&highlight=Nvidia+Feisty)

Never hurts to have a backup of a working xorg.conf:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
```

If you don't have an xorg.conf backed up, press "Ctrl+Alt+F1" when you get the xserver error, then run:
```
sudo dpkg-reconfigure xserver-xorg
```
select "nv" or "vesa" for your video driver.

---

