---
title: "GRUB Options (hd0, etc) please help"
date: 2007-03-08
forum: Installation &amp; Upgrades
---

### Post by maverick280857 on 2007-03-08
PS--Sorry for multiple posts. Request to the moderator: please delete multiple posts.

Hello all

I have recently purchased a HP Pavilion dv6137tx laptop computer. I want to install Ubuntu on an external usb drive. Thankfully, Ubuntu recognizes the drive.

When I start up the installer (Ubuntu live cd), I get the following options as install targets:

/dev/sda: SCSI1 (0,0,0) (sda) - 120.0 GB ATA ST9120822AS (this is the laptop's internal drive)
/dev/sdb: SCSI5 (0,0,0) (sdb) - 40.0 GB ST94011A (this is the external usb drive)

I chose the second one. Then I get a screen which says the following:

--------
[FONT="Courier New"]Language: English
Keyboard Layout: US English
Name: Vivek Saxena
Login Name: vivek
Location: Asia/Calcutta

**GRUB will be installed to (hd0)**

If you continue, the changes listed below will be written to the disks. Otherwise, you will be able to make further changes manually.

WARNING: This will destroy all data on any partitions you have removed as well as on the partitions that are going to be formatted.

The partition tables of the following devices are changed:
SCSI5 (0,0,0) (sdb)

The following partitions are going to be formatted:
partition #1 of SCSI5 (0,0,0) (sdb) as ext3
partition #5 of SCSI5 (0,0,0) (sdb) as swap[/FONT]

---------------------

The query is regarding the line in bold (which refers to GRUB)

Where should I install GRUB? Does hd0 refer to the laptop's internal hard drive? If so, what parameter should I pass here instead of hd0? I don't want to mess with my laptop's internal hdd at all. I just want to boot into ubuntu when I've got the USB drive connected.

Also if you have any other suggestions/ideas/comments, please do write back...would greatly appreciate your help.

Thanks and cheers
vivek

---

### Post by confused57 on 2007-03-08
You might want to read over these 2 threads:
[http://www.ubuntuforums.org/search.php?searchid=15886939](http://www.ubuntuforums.org/search.php?searchid=15886939)

Yes, hd0 is probably your internal drive and you don't want to install grub there, because you wouldn't be able to boot your computer without the external hard drive connected.

You can read through the threads I provided...my suggestion would be to set your bios to boot your USB external hard before your internal hard drive(which should make your external hard drive hd0).

The default on the installer is to put grub onto the mbr of hd0, which should be your external drive, if you have your bios hard drive boot order external first...I think you can actually type in an alternate location to install grub, by clicking on the "box" with hd0, you could change it to **/dev/sdb**, which would be the external hard drive mbr.

---

### Post by maverick280857 on 2007-03-08
Hi confused57, thanks for your reply. Are you sure about /dev/sdb as a possible option? I will try it myself, but I want to make sure I don't spoil the internal drive's contents in any way.

Also, the link you have given in your post does not work.

---

### Post by maverick280857 on 2007-03-14
Ideas? Anyone?

---

### Post by bulldog on 2007-03-14
Make the (hd0)--->(hd1) and it will install on the USB device.

If you want to boot ubuntu,you have to enable 'boot from USB Device' and boot ubuntu.
To boot windows,from GRUB,you'll have to add some lines in your menu.lst.

But I think you'll boot windows from it's own bootloader,otherwise ask on the forum how it's done.

---

### Post by maverick280857 on 2007-03-18
Thanks Bulldog. My intention was to install GRUB not on the MBR of the primary (internal) hdd but rather on the USB. So when I plug in the USB drive and my bios has the USB boot option enabled, I can get into Linux. Otherwise, it'll boot normally into Windoze.

---

