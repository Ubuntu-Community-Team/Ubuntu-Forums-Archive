---
title: "Asus N550JK"
date: 2014-05-28
forum: Installation &amp; Upgrades
---

### Post by Daniel_Mouyal on 2014-05-28
Hello to all Users.

I buy a new Laptop Asus N550JK + I change the hard drive to Samsung 840 SSD 512GB  I install Windows 7 and I create a 15GB Partition for Ubuntu I try to install it on two ways live boot cd + I make USB drive  . The problem that I have is that Ubuntu not recognized the Partition on the SSD is only see the full size of the hard drive as I have only one Partition on the hard drive. I not know what to do I look on different forum bat not find any solution for this  problem I want the tow operating system work I be grateful to how can help me .. if someone can create a video to sow me how to install it or have a guide txt that can help me on this issue

---

### Post by oldfred on 2014-05-28
Boot installer in live mode and post this from the terminal.

sudo parted -l
sudo fdisk -lu

---

