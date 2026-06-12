---
title: "WUBI on USB via GRUB4DOS"
date: 2011-10-18
forum: Installation &amp; Upgrades
---

### Post by treav0r on 2011-10-18
Hello everybody,
I need help because I want to copy my WUBI installation of Kubuntu 10.10 to my USB Key.
My Key is formatted as NTFS.
I want to copy the content of C:\ubuntu\disks\ to my key and chainload the Disks via GRUB4DOS.
Is there a way to load/mount the disk file and chainload Ubuntu?

---

### Post by oldfred on 2011-10-18
Welcome to the forums.

I am no expert on wubi. But saved this link.

See also this thread, you technically do not need windows to use wubi.
Posts by meierfra. to use grub2 to directly boot wubi
[http://ubuntuforums.org/showthread.php?p=8903013](http://ubuntuforums.org/showthread.php?p=8903013)

I do use grub2 to boot ISO on FAT32 and NTFS via loopmount which I think is similar. You just install grub2 to the partition/drive and manually create a grub.cfg file.

MultiBoot USB with Grub2 (boot directly from iso files)
Basically you just install grub2, create a folder for the isos and edit a grub.cfg to loop mount the isos.
HOWTO: Booting LiveCD ISOs from USB flash drive with Grub2
[http://ubuntuforums.org/showthread.php?t=1288604](http://ubuntuforums.org/showthread.php?t=1288604)
[http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1535864](http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1535864)
Install grub2 to USB -general info
[http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB_USB](http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB_USB)

---

### Post by treav0r on 2011-10-20
Did not work.
I installed WUBI into the MBR of my USB Key. (grub4dos-installer => bootfile=wubildr)
Then I got the message "no disk with UUID ...".
I also tried by using "chainloader /wubildr" of grub4dos.

---

### Post by oldfred on 2011-10-20
Small devices like floppy drives and USB flash drive do not have to be partitioned, but flash drives still should be. If you have no UUID did you not partition it first?

---

### Post by treav0r on 2011-11-06
On my key is one partition (NTFS, Created by Paragon Partition Manager).
The WUBI Disk was created on my HDD (NTFS).
I copied it onto my USB key and entered "chainloader /wubildr" in GRUB4DOS".

---

### Post by treav0r on 2011-11-06
Maybe I should create the WUBI Disk on my USB key.

---

### Post by oldfred on 2011-11-06
Have you seen this?

[http://www.pendrivelinux.com/move-wubi-to-a-usb-flash-drive/](http://www.pendrivelinux.com/move-wubi-to-a-usb-flash-drive/)

---

### Post by treav0r on 2011-11-07
I'll try it.

---

### Post by treav0r on 2011-11-08
It works.
I forgot to delete the lines before the linux command.

Thanks

---

