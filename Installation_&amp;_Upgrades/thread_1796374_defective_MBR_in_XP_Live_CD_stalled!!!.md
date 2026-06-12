---
title: "defective MBR in XP Live CD stalled!!!"
date: 2011-07-03
forum: Installation &amp; Upgrades
---

### Post by brian xpsp2 on 2011-07-03
I burnt a ubuntu CD,selected "try Ubuntu"after which it started running,at some point everything stopped,blank screen only the mouse worked.
A similar situation occurred with a "bootmed.isoCD"
This may be connected with the damaged /missing MBR,(I have to boot with a boot floppy containing the necessary files).Is there a distro or other earlier version of ubuntu which will allow me to repair the XP mbr ,,I can't use fdisk /MBR (no XP install/recovery CD)
Most of the internet advice says use a live CD but since I can't get that to work ,what now??
Brian

---

### Post by oldfred on 2011-07-03
Welcome to the forums.

You have two separate but related issues. One seems to be a damaged MBR. And the other is a CD that will not boot. 

You have to get a bootable CD to be able to repair the hard drive. If you system will boot a USB flash drive you can do that also.

Did you burn the CD at the slowest speed possible and verify that is downloaded & was burned correctly. Also check that lens on CD is clean.

You could also download Supergrub which is a smaller liveCD that will boot or repair MBRs.

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)
[http://www.supergrubdisk.org/wiki/Main_Page](http://www.supergrubdisk.org/wiki/Main_Page)
[http://www.supergrubdisk.org/wiki/AutoSuperGrubDisk](http://www.supergrubdisk.org/wiki/AutoSuperGrubDisk)

And windows CD can be used to repair MBR as the code in the MBR is essentially the same. The PBR is different between XP and Vista/7.

If you get Ubuntu to boot, you can install lilo's boot loader which works just like the windows boot loader.

Restore basic windows boot loader - universe enabled
Simply open Synaptic and Settings > Repositories and tick the box against the Universe repo in the Ubuntu Software tab. Close that window and click on reload before installing testdisk with Synaptic.
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
May show error messages about the rest of lilo missing, ignore, we just want MBR with bootloader.

---

### Post by brian xpsp2 on 2011-07-04
Thanks for the info ,
I  don't have an install/repir CD for my XP ,laptop bought secondhand.
I expressly burnt the cd/dvd at low speed using CDburnerXP,and it was also verified,so that is not the problem.I will try your suggestions and update this thread later.
I unfortunately no good experiences with  linux somewhere along the line it always went wrong,going back as far as suse 5 versions so I stayed with MS.thanks anyway.
brian

---

### Post by brian xpsp2 on 2011-07-10
Hallo again,
I downloaded "supergrub"" and used it to try and resyore the XP MBR,however after a restart the laptop still didn't boot.I have solved the problem by using the free programme "test disk" which has a win section with which it is possible to write a "standard" MBR.
thanks anyway
brian

---

