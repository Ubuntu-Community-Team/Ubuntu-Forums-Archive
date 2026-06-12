---
title: "After upgrade, upon boot up, more Ubuntu versions to select now"
date: 2010-12-31
forum: Installation &amp; Upgrades
---

### Post by toolmania1 on 2010-12-31
I upgraded Ubuntu by:

sudo apt-get dist-upgrade

and 

sudo apt-get upgrade

I also updated my software

sudo apt-get update

Both of those upgrade commands were ran on different days.  However, now I have 3 Ubuntu versions I can choose upon start up.  Also, each of those 3 has a recovery mode I can select.  How can I make it so that I only see the one version of Ubuntu?  Or, is this a good thing to be able to go back to the previous version?  What are the pros / cons about the multiple versions being shown upon boot up.  I have always been selecting the newest version.  I think they end in .22, .23, and .24.  ( I cannot see the screen right now, so that is from memory. )

Thanks in advance.

---

### Post by lithopsian on 2010-12-31
Sounds like you have three different kernels now.  Nothing wrong with that, you can leave it if you don't mind the long Grub menu.  Did the upgrade prompt you about the grub menu?

I don't know what version you have, but you can do various things to eliminate  some entries.  One is to get rid of one or more kernels and then update Grub.  You will probably have a linux headers package and a linux image package for each kernel.  I don't suggest you do this though at this stage.  Maybe later.

You can manually edit your grub menu, which will be something like /boot/grub/menu.lst.  Find the entries you don't want to see and comment them out.  If you have deleted the kernels then you could delete the entries.  They aren't too hard to recreate in any case.

---

### Post by r_s on 2010-12-31
use synaptic to delete all previous linux kernel images , except the two newest ones.

---

### Post by presence1960 on 2010-12-31
> **r_s said:**
> use synaptic to delete all previous linux kernel images , except the two newest ones.

Mark for Removal or Complete Removal linux-headers-(kernel #) and linux-image-(kernel #).

The difference is Mark for Complete Removal will remove them from cache, so if you want to reinstall those you will have to download them again.

---

### Post by Sef on 2010-12-31
> sudo apt-get dist-upgrade

and 

sudo apt-get upgrade

Please do not use this as this method is not longer supported. Instead please [read]("https://help.ubuntu.com/community/MaverickUpgrades") this. (Any upgrades are basically the same.)

---

### Post by presence1960 on 2010-12-31
> **Sef said:**
> Please do not use this as this method is not longer supported. Instead please [read]("https://help.ubuntu.com/community/MaverickUpgrades") this. (Any upgrades are basically the same.)

Thanks for that link Sef. Although I never do a dist upgrade (I always do a clean install), I don't want to pass on bad info to someone.

---

