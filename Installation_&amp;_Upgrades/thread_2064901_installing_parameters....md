---
title: "installing parameters..."
date: 2012-09-30
forum: Installation &amp; Upgrades
---

### Post by dawcha on 2012-09-30
I am going to remove my ubuntu installation from the HDD and reinstall it. I have a couple of questions:

1) I want to create 2 partitions one the HDD, one for ubuntu and another for the swap - HDD is 40gb what would be good sizes for the 2 partitions?

2) The ubuntu installer will ask me where I want to install the bootloader (I'm assuming that is the grub bootloader) - I want to install it on my SSD (where win7 is), should I choose sdb or sdb1?

Sorry there are 2 different questions in this post, wasn't sure if they should be a separate post as they both refer to installing ubuntu.

---

### Post by Bashing-om on 2012-09-30
dawcha; Hi ! Welcome to the forum .

Partitions: 40G is good enough ..If you intend to hibernate your machine, standard advise is 2X the amount of ram onboard.

Grub: install it on the device you are booting up (most likely sda, thus grub installs to sda). Check with GParted from the install cd.  If your partitioning scheme HAD a separate /boot partition (advanced stuff) then would the sda1 (partition vice device) come into play.

Windows tools for windows problems, linux tools for ubuntu situations =>If you are going to resize any windows partitions, do so with window's disk utility, prevents other tools from corrupting the windows environment.

See these links as a guide to dual install:
[http://www.linuxbsdos.com/2012/05/17/how-to-dual-boot-ubuntu-12-04-and-windows-7/](http://www.linuxbsdos.com/2012/05/17/how-to-dual-boot-ubuntu-12-04-and-windows-7/)
[https://help.ubuntu.com/community/DualBoot/Windows](https://help.ubuntu.com/community/DualBoot/Windows)
[INDENT]happy ubuntu'n <==BDQ
[/INDENT]

---

