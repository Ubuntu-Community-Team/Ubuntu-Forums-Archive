---
title: "Install a new hard drive"
date: 2010-08-19
forum: Installation &amp; Upgrades
---

### Post by satimis on 2010-08-19
Hi folks,

Old HDD - Seagate 1T SATA II without partition
New HDD - WD Caviar Black, Model: WD1002FAEX
	  1 TB, SATA 6 Gb/s, 64 MB Cache, 7200 RPM
[http://www.wdc.com/en/products/products.asp?DriveID=792](http://www.wdc.com/en/products/products.asp?DriveID=792)

Virtualizer - Orcle VirtualBox (VBox) (Version 3.1.6 r59338 ) (new Version 3.2.8 )


My target to get a new HDD of equal capacity is :-
The VBox was originally installed on the package download on Sun website not on Ubuntu repo.  Therefore I can't run upgrade to install the new version of VBox on repo.
(Remark: I did it before upgrading the new version of VBox on Sun website.  Afterwards it took me several days to fix the problem before the virtual machine can work properly)


Steps to be performed:-

1) Install Ubuntu 10.04 on the new HDD as host and Oracle VBox on repo afterwards
2) copy all VM images (*.vdi) from the old HDD to the new HDD
3) start Oracle VirtualBox and install the new VMs using the all old *vdi images


I hope above steps will work without much problem.  If fail I'll perform following steps to clone the old HDD;

1) connect both new and old HDD to SATA ports
2) start the PC with an installer (Linux)
3) Run following command```

   dd if=/dev/sda of=/dev/sdb

```
4) after cloning finished shutdown the PC and disconnect the old HDD
5) boot the PC
6) start Ubuntu 10.04


Comment and advice would be appreciated.  TIA


This is my first time using WD HDD.  I have been using Seagate HDD for prolonged time.

WD Caviar Black, Model: WD1002FAEX is SATA 3 HDD.  But I'll run it on SATA II port with the pins reset.  I have made some search before.  WD Black series works perfect (of course it can't be compared with SSD and WD VelociRaptor).  I can accept its price which is about 40% more expensive than other brand of equal size.  Neither I would consider adding a PCI-SATA 3 interface card.  I prefer upgrade the complete PC.  1T HDD capacity will be sufficient for my present use.  The old HDD will be reused on another PC (also a virtual machine running KVM/QEMU) which is now running a 600G Seagate HDD.  The 600G Seagate HDD will be used for storage.


B.R.
satimis

---

