---
title: "Trimming Options in GRUB"
date: 2007-06-04
forum: Installation &amp; Upgrades
---

### Post by bdk9246 on 2007-06-04
Hello, 
I have an issue and I am sadly very new to Linux. 
How can I trim the entries in the bootloader?

I'm running Ubuntu Studio, which comes with the low latency kernel- which I will never need. And both generic and LL kernels have just been updated. So, i have about 8 Ubuntu entries before Windows- Which is a problem as this is a family machine and I am the only one who uses ubuntu. 

Can someone please walk me through how to trim my bootloader so it just shows the New Generic kernel and Windows?

Cheers in advance for any help

---

### Post by confused57 on 2007-06-04
Here's everything you always wanted to know about grub, and more:
[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

To edit your menu.lst, open a terminal, enter:
```
cd /boot/grub
sudo cp menu.lst menu.lst_backup
gksudo gedit menu.lst
```

Since it's a family computer, you might want to copy & paste your Window's entry just above the line  ###BEGIN AUTOMAGIC KERNELS LIST...this way Window's would always boot by default, if you have default set to 0.   Put a # in front of all the kernel entries that you do not want displayed in the grub boot menu.

---

### Post by bdk9246 on 2007-06-05
problem solved. 
thanks

---

