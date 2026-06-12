---
title: "boot-repair report on pastebin triple boot issues"
date: 2020-10-22
forum: Installation &amp; Upgrades
---

### Post by wildman36 on 2020-10-22
I have Windows 10 Ubuntu installed to disk 0 (sda) and Fedora 32 installed to disk 1 (sdb)  If i got into the BIOS computer is in UEFI only and there are choices for Fedora, Ubuntu and both hard drives.  If Fedora set to boot first it goes into Fedora grub and Windows is and option.  If Ubuntu is selected to boot first there is no grub and it boot right into Ubuntu.  boot-repair has been run from the live boot-repair distro and I did the terminal chmod commands it instructed me to do but still there is not gurb for Ubuntru.

Here is the [http://paste.ubuntu.com/p/SPDfTWy6WX/](http://paste.ubuntu.com/p/SPDfTWy6WX/)

---

### Post by grahammechanical on 2020-10-22
My guess is that the Ubuntu Grub does not know about Fedora. Load into Ubuntu and run

```
sudo update-grub
```

And see if the printout detects Fedora.

Regards.

---

### Post by oldfred on 2020-10-22
Report for grub in sda5, line 462 & sda8 line 540, your Ubuntu installs show Fedora entries?

Typically Fedora uses LVM as default install.
Ubuntu uninstalls the LVM drivers with an install if LVM is not used as part of the install.
You have to add the lvm2 driver back in & mount the Fedora volumes so os-prober with grub-update in Ubuntu can see the Fedora install.

You show grub installed to the PBR or BS of sda1. That typically breaks NTFS partitions, not sure about FAT32.
I would see the the typical fix for NTFS will work for your FAT32 sda1.
You want to get to this screen:
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery)
select [Advanced] instead of [Analyze] and select [BackupBS]
[HowTo] Repair the bootsector of a Windows partition  - YannBuntu
[https://help.ubuntu.com/community/BootSectorFix](https://help.ubuntu.com/community/BootSectorFix)
[http://ubuntuforums.org/showthread.php?t=1926510](http://ubuntuforums.org/showthread.php?t=1926510)

---

### Post by wildman36 on 2020-11-02
I found it, sorry for the repeat post but i'm sure the pastebin is totally different now from me messing things up.

---

### Post by wildman36 on 2020-11-02
Okay, I'm there, you said to mount the Fedora partitions, right?  How and where?  sudo mount /dev/sdb1 /mnt/?  I don't  understand really what your talking about when you say LVM, LVM2, PBR and BS, I'm lost.  And when I was in TestDisk and did Advanced then next option was to take an image or sda or sdb.  All the partitions look to be mounted already to /mnt/boot-sav/ except sda2 which is a windows partition, Microsoft Reserved I think, and sdb3 which is Fedora home.  Now on sdb1 in the EFI folder there is BOOT, fedora and ubuntu.  but on Ubuntu sda5 there is crazy stuff like /mnt/boot-sav/sda5/mnt/boot-sav/sdb1 and that is empty

---

### Post by wildman36 on 2020-11-02
[http://paste.ubuntu.com/p/bm3F85rYjt/](http://paste.ubuntu.com/p/bm3F85rYjt/)

This is where I'm at.

---

### Post by oldfred on 2020-11-02
Your Fedora is using LVM, Logical Volumes. 
That in effect uses one partition and then lets you have volumes inside that one partition.

Ubuntu can use LVM, but if not used, the installer uninstalls the LVM driver. So you have to reinstall it to be able to see Fedora from Ubuntu.
LVM Advantages/Disadvantages Post #9
[http://ubuntuforums.org/showthread.php?t=1586328&p=9917145#post9917145](http://ubuntuforums.org/showthread.php?t=1586328&p=9917145#post9917145)
[https://wiki.ubuntu.com/Lvm](https://wiki.ubuntu.com/Lvm)
[https://wiki.archlinux.org/index.php/LVM](https://wiki.archlinux.org/index.php/LVM)

sudo apt-get install lvm2
sudo fdisk -l
sudo pvdisplay
sudo lvdisplay

Report shows this as Fedora's LVM root volume, see line 651 for its mount of your volumes.
/dev/fedora_localhost-live/root

---

