---
title: "need help installing windows xp"
date: 2013-08-18
forum: Installation &amp; Upgrades
---

### Post by sonicla18 on 2013-08-18
i need help i cant seem to be able to install windows xp onto my pc that is running lubuntu/ubuntu. it is an acer aspire one with no disk drive so i have to use a usb and i have already created a bootable usb with windows xp on it but when i run the installation the pc partition doesnt appear only the usb partition. Can someone help?

---

### Post by oldfred on 2013-08-18
Windows does not see Linux partitions. 
You need to use a Linux live installer with gparted to create a primary NTFS partition with the boot flag.

       [http://partedmagic.com/](http://partedmagic.com/)
[http://gparted.sourceforge.net/faq.php](http://gparted.sourceforge.net/faq.php)

Ubuntu installer also has gparted, but you cannot run gparted from your working install or any mounted partitions. You may also have to unmount swap if using Ubuntu liveCD.

---

### Post by sonicla18 on 2013-08-18
i have already tried gparted and created an ntfs partition with boot flag and the partition still will not appear. the acer aspire one does not have a disk drive im doing it all through usb

---

### Post by oldfred on 2013-08-18
Is it a primary partition?

Post these:

sudo parted -l
sudo fdisk -lu

---

### Post by Lim_Xiang_Yann on 2013-08-19
For me, I will use gparted to get some free space for xp
then, DON'T allocate it in linux
use the XP installer to create a partition

---

### Post by sonicla18 on 2013-08-20
i have found the solution to my problem and installed windows xp, but thank you for trying to help me

---

### Post by rafiqcombrinck on 2013-08-20
Yeah, I had the same issue, took me months (on/off) to figure it out. I eventually found that WinXP does not have built in drivers that support AHCI so you had 2 options. You could set your BIOS to IDE and install WinXP, which will leave you linux'less, or you can leave the BIOS on AHCI and use an app called nLite to simply streamline your pc's drivers into a WinXP ISO (the one you would have used to create the bootable usb stick) and viola. As for creating the bootable usb stick, the only app I could find that worked properly was WintoFlash, just be forwarned that it loads an array of rubbish on the pc you are creating the usb stick on.

Found Yumi Multiboot installer this morning ... works much better than WintoFlash.

---

### Post by steve63752 on 2013-09-11
Easy2Boot (free) will install from a vanilla unmodified XP Install ISO to any AHCI (or SCSI or RAID) target computer. It automatically creates the correct F6 virtual floppy disk for your hardware and you don't even need to press F6. It will also install from any Vista/win7/win8 Install ISOs as well.
[http://www.youtube.com/watch?v=MBKh_jDyTmQ](http://www.youtube.com/watch?v=MBKh_jDyTmQ)

---

