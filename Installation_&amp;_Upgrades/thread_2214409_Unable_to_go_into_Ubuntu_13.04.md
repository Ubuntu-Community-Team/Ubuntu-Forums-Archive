---
title: "Unable to go into Ubuntu 13.04"
date: 2014-04-01
forum: Installation &amp; Upgrades
---

### Post by Indranil_Basu on 2014-04-01
Hello,

I have a PC with Windows 7. 

A few days back I installed Ubuntu 13.04, but I am unable to boot into Ubuntu 13.04.

Whenever I am switching on my PC it is directly booting with Windows 7.

I have created the following partitions for Ubuntu 13.04
/boot
/
/home
/swap

And pointed the boot partition to the /boot of my sda.

On doing some Google search I found a grub menu editor for windows 7, however I have followed the steps to add a menu for Ubuntu launching. But on clicking the Ubuntu in the menu it is opening a linux console but not launching the complete Ubuntu OS.

Can you guys help me to sort out this problem?

With regards,
Indranil

---

### Post by coffeecat on 2014-04-01
A few comments.

Ubuntu 13.04 is past end-of-life and you wouldn't be able to update it even if you were able to fix it. Well - you could with a special repository but in my opinion it is not worth the trouble. Since you have a non-functioning installation I would suggest starting over with a fresh installation of Ubuntu 13.10 which you will be able to upgrade to the long-term support 14.04 version by the end of this month.

A separate boot partition is an unnecessary complication. If you want a straightforward dual boot with Windows on a relatively recent set of hardware I can think of no reason for having a separate boot partition.

If you need help sorting out your partitions or how to best install 13.10 using the Linux partitions you already have, please boot up with a live CD or USB of Ubuntu and post the output of this terminal command:

```
sudo fdisk -l
```

And also post a screenshot of an open Gparted window. You can get a screenshot of an application window with alt+PrintScrn.

---

