---
title: "How To Triple Boot Ubuntu With Windows Vista And An Earlier Version Of Windows"
date: 2010-01-26
forum: Installation &amp; Upgrades
---

### Post by erictherev on 2010-01-26
**You Will Need:**
Destination Computer (I used an Acer Aspire One 0751-h Netbook)
Ubuntu CD (I used Kubuntu 9.10)
Windows Vista or Windows 7 CD
Installation discs for the older version of Windows
PartEd Magic [(freeware - available here)]("http://partedmagic.com/download.html")

**Preparation:**
The first thing you need to do is partition your drive(s). I wanted 4Gb swap on sda2, 40Gb NTFS on sda3, 40Gb ext4 on sda4 and the remainder as NTFS on sda1. I will be using sda as my hard drive, but if you have an IDE drive, you'll want to substitute hda.

**Partitioning:**
1)Boot into PartEd Magic. Once the system is completely booted, open the partition editor (gparted). Not wanting to do a lot of math to set up my drives, I started at the end of the drive and worked my way to the beginning.

2)After allocating disc space, you may need to reassign your drives. I had sda4, sda3, sda2, and sda1. (In that order.) To do this, I removed sda4 and sda1, then reassigned what was formerly sda4 as sda1. Complicated, I know, but we want to ensure that Windows Vista (or 7) goes on sda1.
 
3)Once you have your drive space allocated the way you want it, click on Edit and apply all changes, then exit the partition editor.
 
4)Open RoxTerm.  Enter the following commands:

```
fdisk /dev/sda
p *(prints your partition table)*
a *(flag a partition as boot)*
3 *(Will vary according to your partition table. This is the partition you want your older Windows OS on)*
p
a *(This step and the next only apply if you have more than one partition flagged.)*
1 *(see above)*
```
You should now have only the partition your old Windows OS will go on flagged.
```
w *(Write the changes.)*
```

**Installation:**
5)Reboot and install your Old Windows OS.
 
6)Reboot  into PartEd Magic and set sda1 as flagged, unset sda3 (or whereever your old Windows OS resides).
 
7)Reboot and install Windows Vista (or Windows 7).

8)Reboot and install Ubuntu.

You should now have a fully functional triple-boot system that will boot any of these OS's from Grub.

---

