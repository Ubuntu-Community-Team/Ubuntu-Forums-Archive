---
title: "Video Card support"
date: 2011-02-14
forum: Installation &amp; Upgrades
---

### Post by sjkregs on 2011-02-14
Can someone please explain to me why the iso's for pclinuxos and Puppy comes with support  for Intel and Nvidia video drivers, but Ubuntu does not??

Thanks

---

### Post by mikewhatever on 2011-02-14
... but it does. Both Intel and Nvidia cards work out of the box in Ubuntu.

---

### Post by realzippy on 2011-02-14
ubuntu also supports nvidia:
 click, reboot,done.
In puppy + pclinuxos the proprietary driver is preinstalled ?

---

### Post by sjkregs on 2011-02-14
> **realzippy said:**
> ubuntu also supports nvidia:
 click, reboot,done.
In puppy + pclinuxos the proprietary driver is preinstalled ?

Starting with Ubuntu 10.04 my laptop with intel video drivers and my desktop with nvidia drivers does not boot off of the live cd/dvd iso on ubuntu, kubuntu, xubuntu, mint and several other distros I have tried, but with work like a charm with all variations of pclinuxosand puppy.They will work using virtual box but blank screen with live  cd/dvd.

---

### Post by Frogs Hair on 2011-02-14
My Nvidia card worked out of the box with 3 different Ubuntu releases , but adding the proprietary driver was my choice since there is more than one driver available for my card on Ubuntu.

I have seen proprietary drivers added to video card installation discs for windows , but they're usually out of date by the time the card is sold.

---

### Post by sjkregs on 2011-02-14
> **Frogs Hair said:**
> My Nvidia card worked out of the box with 3 different Ubuntu releases , but adding the proprietary driver was my choice since there is more than one driver available for my card on Ubuntu.

I have seen proprietary drivers added to video card installation discs for windows , but they're usually out of date by the time the card is sold.


Is there a  way to manually add video drivers to the iso so that i can run the live cd/dvd?

---

### Post by Frogs Hair on 2011-02-14
> **sjkregs said:**
> Is there a  way to manually add video drivers to the iso so that i can run the live cd/dvd?

I don't if it is possible with Remastersys or not , but you could do some research . Another reason proprietary are not added is they not open source and can't be redistributed .[U][http://www.geekconnection.org/remastersys/](http://www.geekconnection.org/remastersys/)
[/U]

---

### Post by mikewhatever on 2011-02-15
> **sjkregs said:**
> Starting with Ubuntu 10.04 my laptop with intel video drivers and my desktop with nvidia drivers does not boot off of the live cd/dvd iso on ubuntu, kubuntu, xubuntu, mint and several other distros I have tried, but with work like a charm with all variations of pclinuxosand puppy.They will work using virtual box but blank screen with live  cd/dvd.

It would be interesting to know what the GPUs are. Can you run **lspci** on Puppy or PClinux and post the output.

---

### Post by realzippy on 2011-02-15
*Is there a way to manually add video drivers to the iso so that i can run the live cd/dvd?*

Think it is possible generally,but I know that it does not work with remastersys;you had to include the nvidia kernel modules,blacklist noveau aso...

Edit:
[http://www.justlinux.com/forum/showthread.php?t=153113](http://www.justlinux.com/forum/showthread.php?t=153113)   might help....

[http://ubuntuforums.org/showthread.php?t=1644967](http://ubuntuforums.org/showthread.php?t=1644967)   also.BTW,lots of hits googling "ubuntu include nvidia driver live CD"   ;-)

---

