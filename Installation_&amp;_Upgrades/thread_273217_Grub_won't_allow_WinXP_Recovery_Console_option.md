---
title: "Grub won't allow WinXP Recovery Console option"
date: 2006-10-07
forum: Installation &amp; Upgrades
---

### Post by RealGomer on 2006-10-07
I need to run the WXP Recovery Console inorder to run fixmbr. I had loaded Ubuntu Linux onto a separate partition with GRUB being the boot manager. I can't get into Recovery Console from the OS disc included with my notebook. Running e:\i386\WINNT32.EXE /cmdcons doesn't bring up the recovery console option. The only OS disc I have is the Operating System Disk Gateway pressed for my laptop. The laptop is runnignWinXP Media Center Edition so I can't get to Recovery console from my WinXP Pro disk.
Suggestions?

---

### Post by kidders on 2006-10-07
I don't quite follow the problem you're having ... can't you boot your system with a recovery CD and go from there?

---

### Post by RealGomer on 2006-10-08
Well, the recovery disk that came with the notebook is one of those crippled disks that will only let you reinstall the friggin' OS. I've now a second reason to uninstall Ubuntu. The first is I couldn't get the Broadcom 4818 (?) 802.11G chip set to work. Now, when I do select Ubuntu from the GRUB, it gets hung at Loading Manual Drivers. So, I have to figure out how to make a boot disk for the WinXP Media Edition software. And Gateway says tough noogies because of the EULA.

---

### Post by kidders on 2006-10-09
You should be able to download boot floppies or a  CD from someplace ... there are plenty of repositories for these sorts of things. It's a pity Ubuntu didn't work out for you :-(

---

### Post by gonesolo on 2006-10-09
for the boot disk try [www.bootdisk.com](www.bootdisk.com). they have loads of boot disks there you should be able to find one to help you. 

Why are Gateway being so unhelful? 

Question: if you can't boot from the CD how are you suppose to reinstall the OS if you format the hard disks???

---

### Post by gn2 on 2006-10-11
> **gonesolo said:**
> for the boot disk try [www.bootdisk.com](www.bootdisk.com). they have loads of boot disks there you should be able to find one to help you. 

Why are Gateway being so unhelful? 

Question: if you can't boot from the CD how are you suppose to reinstall the OS if you format the hard disks???

You contact the system vendor who will sell you a CD. 

It's a well known scam.

There are downloadable boot utilities that will let you "fixmbr" without having to buy a CD.

You can always ask a friend to borrow their Windows install CD?
.

---

### Post by dragonflyseven on 2006-10-15
If all you want to do is boot into safe mode, hit F8 immediatly after selecting XP in GRUB. In safe mode, you can enter the "roll back" feature.

---

