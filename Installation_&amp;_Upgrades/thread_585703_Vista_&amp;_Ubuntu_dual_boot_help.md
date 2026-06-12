---
title: "Vista &amp; Ubuntu dual boot help"
date: 2007-10-21
forum: Installation &amp; Upgrades
---

### Post by laluckaryves on 2007-10-21
Hey guys i'm having trouble setting up a dual boot with vista and ubuntu 7.10. I have two hard drives: 320gb for extra storage (drive 0) and 320gb with windows (drive 1). I partitioned the drive with windows and shrunk the main volume by 12gb to make room for linux. Then i booted from the live cd and went through the install process. I start getting unsure when it comes to partitioning... i chose the manual option and then split the unallocated space into two new partitions: 10gb root partition ("/") and a 2gb swap partition. Then skipping to the end of the install there is an advanced tab which determines where GRUB is installed. On that same page it reads something like:

sdb: 
partition #3: ext3 (root partition im assuming)
partition #5: swap file

In the advanced tab i changed it from the default value of (hd0) to (hd1,2) because i'm installing linux on my second hard drive and the root file is in the third partition.
After the installation is comlplete it says to reboot but when i do it goes straight into windows vista without any GRUB menu or way to decide which OS to boot. Where did i go wrong? Any help would be great! thanks

---

### Post by por100pre1 on 2007-10-22
Everything seems fine, the Vista boot loader is working as usual in a Vista installation. Use [EasyBCD]("http://neosmart.net/dl.php?id=1") to add Ubuntu to Vista's boot loader. Because you installed GRUB in Ubuntu's root partition, EasyBCD will do the trick.

---

### Post by laluckaryves on 2007-10-23
I have tried EasyBCD countless times and everytime i get an error that says something like unable to boot insert system disk and press enter. Any ideas? Can anyone give me detailed instructions on setting up BCD? I just add a new entry and direct it to the partition i chose to install GRUB/Ubuntu to. Thanks

---

### Post by por100pre1 on 2007-10-24
Weird, how many partitions do you have in the second hard disk drive? If you only have Ubuntu then grub should have been installed in (hd1,0) and not in (hd1,2). The method of adding Linux entry should have worked with EasyBCD... :-k

---

### Post by Computer Guru on 2007-10-26
If you use [EasyBCD 1.7]("http://neosmart.net/dl.php?id=1") (the latest version), there is an option when adding a Linux entry called "GRUB isn't installed to the bootsector." 

If you check this checkbox *then* add the Linux entry, EasyBCD will try to boot into Ubuntu in "GRUBless-Linux" mode, where it'll search for Ubuntu and load it for you without any intervention or configuration on your behalf.

---

