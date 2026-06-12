---
title: "32 gb persistent pendrive with greater tha 4 gb persistant space"
date: 2016-10-03
forum: Installation &amp; Upgrades
---

### Post by shubham-sharmaa001 on 2016-10-03
please help me to create a bootable persistant ubuntu pendrive with greater than 4gb casper-rw partition.i have followed steps to create a partition named casper-rw whenever i do it it doesn't boot.

---

### Post by howefield on 2016-10-03
Hello and welcome to the forums, as your thread is not a Tutorial, it has been moved to the "*Installation & Upgrades*" forum.

---

### Post by ajgreeny on 2016-10-03
You do not say where you found the info about making a separate partition for persistence, so just in case it was some outside source, have a look at [https://help.ubuntu.com/community/LiveCD/Persistence](https://help.ubuntu.com/community/LiveCD/Persistence)

If this was the info you found I don't think I can help you any further but others may be able to, so hang around for a while and if you get no help after 24 hours bump the thread with a reply post containing the word "Bump".

---

### Post by ubfan1 on 2016-10-03
Take a look at mkusb, it might offer persistence.  The problem with the older docs is the change in the way the Ubuntu ISO is made -- it now has a link, which cannot be put onto a FAT filesystem, so the read-only ISO9660 filesystem is used on the USB.  The edits necessary to grub.cfg, adding the word "persistent" to the linux line, cannot be done on a read-only filesystem.  The Statup Disk Creator has had the "persistence" removed awhile ago.  
  On UEFI machines, you can easily copy the ISO files (less the link) to a FAT fs USB, and edit the grub.cfg to remove the preseed argument on the linux line.  This boots successfully, but I haven't tested persistence on one yet.  Anyway, to sum up:
Possible Solutions:
 1) Remake the ISO with the grub.cfg and txt.cfg files edited to
include the word persistence, and either include a casper-rw file 
or a partition labeled casper-rw.  Edit the syslinux files too if you need the legacy boot. (txt.cfg?)
 2) Opt for UEFI only, without the preseed capability.  This only uses grub.
Make a FAT partition/filesystem, and copy the files from the loop mounted ISO.
The link "ubuntu" will fail of course.
Edit the grub.cfg, adding the words
"persistent live-media-path=/casper ignore_uuid" and removing 
"file=/cdrom/preseed/ubuntu.seed".  Now make a casper-rw file or a casper-rw
partition. (untested)
 3) Use DD, edit the partition table to add another ext2 partition and label it casper-rw.
Edit the grub.cfg file and txt.cfg to add the word persistent. (May not be possible, those files
are on a iso9660 fs. but a hex/binary editor may allow replacing the "quiet splash")
 4) Put the ISO onto a USB FAT fs, and boot it directly.  Have a casper-rw in that fs or a labeled partition. This is the technique used for multi-boots, so is probably the best approach currently.

---

### Post by C.S.Cameron on 2016-10-03
I have spent a bit of time trying to get persistent partitions working with 16.04, 64 bit.
(I think they work with 32bit)
No success using SDC or UNetbootin.
Iso/grub 2, (MultiBootUSB), works as does mkusb.
Mkusb is simplest to use and automatically makes a casper-rw partition.
A home-rw partition can be installed manually.

---

### Post by sudodus on 2016-10-05
Welcome to the Ubuntu Forums *shubham-sharmaa001* :-)

I think it will work with mkusb according to the following links

[https://help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb)

[mkusb/persistent](https://help.ubuntu.com/community/mkusb/persistent)

You will have a choice to select the percentage for persistence - to share the available space between a casper-rw partition for persistence and a usbdata partition with the NTFS file system for exchange of data with Windows. For example, if you select 67 %, 2/3 [of the available space] will be used for persistence, in your case with a 32 GB pendrive, around 20 GB (and 10 GB for usbdata; some drive space is used for the image of the iso file). You may select 100% for persistence.

You may also consider an installed system (in the USB pendrive), for example according to the following links,

[Try Ubuntu (Kubuntu, Lubuntu, Xubuntu, ...) before installing it](http://ubuntuforums.org/showthread.php?t=2230389)

[Installation/UEFI-and-BIOS](https://help.ubuntu.com/community/Installation/UEFI-and-BIOS)

Good luck :-)

---

