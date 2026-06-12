---
title: "Ubuntu 11.04, not working for me (and others)"
date: 2011-05-12
forum: Installation &amp; Upgrades
---

### Post by ideasbuenas on 2011-05-12
Yday, I was trying to reinstall Ubuntu 11.04 on my previously destroyed HDD (by my Ubuntu mistakes). So I use a script to learn WTF'd happened. I show u:

Boot Info Script 0.55 dated February 15th, 2010 

============================= Boot Info Summary: ==============================
 
 => Grub 2 is installed in the MBR of /dev/hda and looks for b2d.
 
 hda1: __________________________________________________ _______________________
 
 File system: Extended Partition
 Boot sector type: -
 Boot sector info: 
 
 hda5: __________________________________________________ _______________________
 
 File system: 
 Boot sector type: -
 Boot sector info: 
 Mounting failed:
 mount: unknown filesystem type ''
 
 hda6: __________________________________________________ _______________________
 
 File system: 
 Boot sector type: -
 Boot sector info: 
 Mounting failed:
 mount: unknown filesystem type ''
 mount: unknown filesystem type ''
 
 hda2: __________________________________________________ _______________________
 
 File system: ntfs
 Boot sector type: Windows XP
 Boot sector info: No errors found in the Boot Parameter Block.
 Operating System: Windows XP
 Boot files/dirs: /boot.ini /ntldr /NTDETECT.COM
 
 hdc: __________________________________________________ _______________________
 
 File system: iso9660
 Boot sector type: -
 Boot sector info: 
 Operating System: 
 Boot files/dirs: 
 
 =========================== Drive/Partition Info: =============================
 
 Drive: hda ___________________ __________________________________________________ ___
 
 Disk /dev/hda: 81.9 GB, 81964302336 bytes
 255 heads, 63 sectors/track, 9964 cylinders, total 160086528 sectors
 Units = sectors of 1 * 512 = 512 bytes
 Disk identifier: 0x7e3b7e3b
 
 Partition Boot Start End Size Id System
 
 /dev/hda1 2,046 20,514,815 20,512,770 5 Extended
 /dev/hda5 2,048 18,534,399 18,532,352 83 Linux
 /dev/hda6 18,536,448 20,514,815 1,978,368 83 Linux
 /dev/hda2 * 20,515,005 160,071,659 139,556,655 7 HPFS/NTFS
 
 
 blkid -c /dev/null: __________________________________________________ __________
 
 Device UUID TYPE LABEL 
 
 /dev/hda2 AAD83924D838F065 ntfs 
 /dev/hdc iso9660 SLAX 
 
 ============================ "mount | grep ^/dev output: ===========================
 
 Device Mount_Point Type Options
 
 aufs / aufs (rw)
 /dev/hda2 /mnt/hda2 fuseblk (rw,noatime,allow_other,blksize=4096)
 
 
 ================================ hda2/boot.ini: ================================
 
 [boot loader]
 timeout=15
 default=multi(0)disk(0)rdisk(0)partition(1)\WINDOW S
 [operating systems]
 multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Micro soft Windows XP Professional" /noexecute=optin /fastdetect
 multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Micro soft Windows XP Professional" /noexecute=optin /fastdetect
 
 ==================== hdc: Location of files loaded by Grub: ====================
 
 
 .0GB: boot/initrd.gz
 .0GB: boot/vmlinuz
 =======Devices which don't seem to have a corresponding hard drive==============
 
 hdd 
 =============================== StdErr Messages: ===============================
 
 File descriptor 11 left open
 No volume groups found
 mdadm: No arrays found in config file
 

MAYBE if someone who knows about partitioning is reading this and wants to give me a little help I will surely reward (him or her) in return for a well service rendered. Thanks a lot.

---

### Post by Elfy on 2011-05-12
Thread closed. Please do not post duplicates, it dilutes community effort.

---

