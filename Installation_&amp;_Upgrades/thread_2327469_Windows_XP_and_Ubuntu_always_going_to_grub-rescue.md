---
title: "Windows XP and Ubuntu always going to grub-rescue"
date: 2016-06-11
forum: Installation &amp; Upgrades
---

### Post by Stu_L on 2016-06-11
Hi all,

I've recently dug out an old desktop out for a family member who wanted to use some old XP only programs (and it's not really fast enough to run XP in a VM). So I installed XP and all was working well.
I then tried to install Ubuntu and later Zorin Lite also alongside XP so they could safely use the 'net, with separate partitions for root,home and swap. Unfortunately whatever I try I cannot get grub to work properly.

If I repair the MBR (using the lilo fixmbr option) then Windows will boot fine, however the second I either manually or using boot-repair (from a live cd) put grub back in I get the "grub rescue" screen upon boot.

Windows is on sda1 and linux root (inc. boot) on sda2.

Any ideas anyone of what might be wrong? I'm guessing it's something obvious? Is it a BIOS issue?

Thanks in advance, Stu

I've included my boot-repair script here [http://paste2.org/PcpzmpPY](http://paste2.org/PcpzmpPY)

Boot Info Script cfd9efe + Boot-Repair extra info [Boot-Info 26Apr2016]


============================= Boot Info Summary: ===============================

=> Grub2 (v2.00) is installed in the MBR of /dev/sda and looks at sector 1 of
the same hard drive for core.img. core.img is at this location and looks
for (,msdos2)/boot/grub. It also embeds following components:

modules
---------------------------------------------------------------------------
fshelp ext2 part_msdos biosdisk
---------------------------------------------------------------------------

sda1: __________________________________________________ ________________________

File system: ntfs
Boot sector type: Windows 2000/XP: NTFS
Boot sector info: No errors found in the Boot Parameter Block.
Operating System: Windows XP
Boot files:

sda2: __________________________________________________ ________________________

File system: ext4
Boot sector type: -
Boot sector info:
Operating System: Zorin OS 9
Boot files: /boot/grub/grub.cfg /etc/fstab
/boot/grub/i386-pc/core.img

sda3: __________________________________________________ ________________________

File system: ext4
Boot sector type: -
Boot sector info:
Operating System:
Boot files:

sda4: __________________________________________________ ________________________

File system: swap
Boot sector type: -
Boot sector info:

============================ Drive/Partition Info: =============================

Drive: sda __________________________________________________ ___________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition Boot Start Sector End Sector # of Sectors Id System

/dev/sda1 * 63 19,531,312 19,531,250 7 NTFS / exFAT / HPFS
/dev/sda2 19,531,776 39,063,551 19,531,776 83 Linux
/dev/sda3 39,063,552 58,595,327 19,531,776 83 Linux
/dev/sda4 58,595,328 66,408,447 7,813,120 82 Linux swap / Solaris


"blkid" output: __________________________________________________ ______________

Device UUID TYPE LABEL

/dev/loop0 squashfs
/dev/sda1 F6787C48787C099F ntfs
/dev/sda2 a4714089-b267-40fc-abee-7693a3cc807e ext4
/dev/sda3 f8ade0c7-b5b6-4b06-bf3f-c8f8d155b007 ext4
/dev/sda4 26bd039f-6add-4d57-a7d7-f4cf2747a6a4 swap
/dev/sr1 iso9660 Zorin OS 9 Lite 32 bit
/dev/zram0 36d7a9d4-b414-452f-a269-7170f6513f19 swap



Also what grub rescue shows here also: [https://ibin.co/2kH6DjjnG0Ud.jpg](https://ibin.co/2kH6DjjnG0Ud.jpg)
[IMG]https://ibin.co/2kH6DjjnG0Ud.jpg[/IMG]

---

