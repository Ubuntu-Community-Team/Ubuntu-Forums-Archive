---
title: "Minor annoyance at boot"
date: 2007-12-22
forum: Installation &amp; Upgrades
---

### Post by jw1405 on 2007-12-22
I get this message each time I boot. 

 * checking file system
fsck 1.40.2 (date)
Failed to open device 'UUID=583485df-6EF1-4CEF-bb26-36c60a7c14a7': no such file or directory

fscheck died with exit status 8

* File system check failed
Alog is being saved in /var/log/fsck/checkfs if that location is writable. please repair the file manually.

This is content of file. 

Log of fsck -C -R -A -a 
Sat Dec 22 16:55:22 2007

fsck 1.40.2 (12-Jul-2007)
Failed to open the device 'UUID=583485df-6ef1-4cef-bb26-36c60a7c14a7': No such file or directory


fsck died with exit status 8

Sat Dec 22 16:55:22 2007
----------------

  What should this file contain, or what additional info do you need. 
                                            please Help, thank you.

---

### Post by heatpumpcontrol on 2007-12-22
list your contents of:
sudo blkid

gksudo gedit /etc/fstab

---

### Post by jw1405 on 2007-12-22
output for sudo blkid:

/dev/sda1: UUID="5bfa210d-d8ce-40df-a265-bff58b4b055c" TYPE="reiserfs" 
/dev/sda5: TYPE="swap" 
/dev/sda6: UUID="2afe4b19-da03-4178-9bf1-0d21549e3b75" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda3: UUID="7bab20bb-a977-4004-9b75-3b5c8b74d8fd" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda4: UUID="75d45c12-7f23-422a-b39c-272d893e691c" TYPE="reiserfs"

output of gksudo gedit /etc/fstab:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=5bfa210d-d8ce-40df-a265-bff58b4b055c /               reiserfs notail          0       1
# /dev/sda6
UUID=583485df-6ef1-4cef-bb26-36c60a7c14a7 /Home           reiserfs defaults        0       2
# /dev/sda5
UUID=4c36a39f-0868-4cd5-96b1-e80994d7615e none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto,exec 0       0

---

### Post by heatpumpcontrol on 2007-12-22
ok how about your fstab?

---

### Post by heatpumpcontrol on 2007-12-22
ok how about your fstab? disregard.. let me see now.

---

### Post by heatpumpcontrol on 2007-12-22
> **jw1405 said:**
> output for sudo blkid:

/dev/sda1: UUID="5bfa210d-d8ce-40df-a265-bff58b4b055c" TYPE="reiserfs" 
/dev/sda5: TYPE="swap" 
/dev/sda6: UUID="2afe4b19-da03-4178-9bf1-0d21549e3b75" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda3: UUID="7bab20bb-a977-4004-9b75-3b5c8b74d8fd" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda4: UUID="75d45c12-7f23-422a-b39c-272d893e691c" TYPE="reiserfs"

output of gksudo gedit /etc/fstab:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=5bfa210d-d8ce-40df-a265-bff58b4b055c /               reiserfs notail          0       1
# /dev/sda6
UUID=583485df-6ef1-4cef-bb26-36c60a7c14a7 /Home           reiserfs defaults        0       2
# /dev/sda5
UUID=4c36a39f-0868-4cd5-96b1-e80994d7615e none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto,exec 0       0

change your fstab to the following:

First do a 
sudo cp /etc/fstab /etc/fstab.bak

now 
gksudo gedit /etc/fstab

enter the following:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=5bfa210d-d8ce-40df-a265-bff58b4b055c /               reiserfs notail          0       1
# /dev/sda6
UUID=2afe4b19-da03-4178-9bf1-0d21549e3b75 /Home           reiserfs defaults        0       2
# /dev/sda5
UUID=4c36a39f-0868-4cd5-96b1-e80994d7615e none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto,exec 0       0

Your /dev/sda6 had the wrong info in your fstab. That is all that has to be changed. Reboot

---

### Post by jw1405 on 2007-12-22
New error message:

reiserfs_open : the reiserfs super block cannot be found on /dev/sda6. 
Failed to open the file system.

If the partition is valid and it really contains the reiserfs partition, then the superblock is corrupted and you need to run this utility with --rebuild-sb

---

### Post by logos34 on 2007-12-22
I think the fs type is wrong.  

> /dev/sda6: UUID="2afe4b19-da03-4178-9bf1-0d21549e3b75" SEC_TYPE="ext2" TYPE="ext3" 

Change sda6 line  to this:

> # /dev/sda6
UUID=2afe4b19-da03-4178-9bf1-0d21549e3b75 /Home [COLOR="Red"]ext3[/COLOR] defaults 0 2

---

### Post by jw1405 on 2007-12-22
Thank you for the feed back. I made the change now waiting for automatix2 to finish downloading to reboot. But I think that will fix it.

---

### Post by jw1405 on 2007-12-22
Success!  No error on boot, thank you both.

---

