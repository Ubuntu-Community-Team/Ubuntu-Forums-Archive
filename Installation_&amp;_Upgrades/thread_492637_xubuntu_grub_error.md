---
title: "xubuntu grub error"
date: 2007-07-04
forum: Installation &amp; Upgrades
---

### Post by pookerpuff on 2007-07-04
im running windows vista on an acer aspire 3680 and decided to install xubuntu onto my 160Gb seagate Freeagent go portable hard drive.everything went great i read up on the process and when it came time to install i had no problems.my external drive popped up as sdb instead of sda as most posts suggested it would so i modified the instructions changing everything to accomodate.it all went well until i had to reboot.it gave me grub error 17.can anyone help?

---

### Post by confused57 on 2007-07-05
> **pookerpuff said:**
> im running windows vista on an acer aspire 3680 and decided to install xubuntu onto my 160Gb seagate Freeagent go portable hard drive.everything went great i read up on the process and when it came time to install i had no problems.my external drive popped up as sdb instead of sda as most posts suggested it would so i modified the instructions changing everything to accomodate.it all went well until i had to reboot.it gave me grub error 17.can anyone help?
Did you install grub to the external drive, i.e. can you boot your internal hard drive with the external hard drive disconnected?

You might want to boot up the live cd, open a terminal(Applications---Accessories---Terminal), post the output of:
```
sudo fdisk -l
```
-l is a lowercase "L"

You can also use the live cd to mount your Ubuntu partition and post the output of your menu.lst:
[http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD](http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD)

---

### Post by pookerpuff on 2007-07-05
i can load vista without a problem so long as my external  drive isnt connected.
as instructed:
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1019     8185086   27  Unknown
/dev/sda2   *        1020        5394    35142187+   6  FAT16
/dev/sda3            5395        9729    34820887+   7  HPFS/NTFS

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       18893   151757991   83  Linux
/dev/sdb2           18894       19457     4530330    5  Extended
/dev/sdb5           18894       19457     4530298+  82  Linux swap / Solaris
i could not mount the way the page instructed.

---

### Post by confused57 on 2007-07-05
> **pookerpuff said:**
> i can load vista without a problem so long as my external  drive isnt connected.
as instructed:
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1019     8185086   27  Unknown
/dev/sda2   *        1020        5394    35142187+   6  FAT16
/dev/sda3            5395        9729    34820887+   7  HPFS/NTFS

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       18893   151757991   83  Linux
/dev/sdb2           18894       19457     4530330    5  Extended
/dev/sdb5           18894       19457     4530298+  82  Linux swap / Solaris
i could not mount the way the page instructed.

If you're getting a grub boot menu, highlight your Ubuntu entry, press "e" to edit, then change root from (hd1,x) to (hd0,x), then press "b" to boot...this is temporary, but can be made permanent if it works.

You might want to burn a copy of the Super Grub Disk if you're not getting a grub boot menu:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

---

### Post by pookerpuff on 2007-07-05
that worked now how do i make it a permanent fix?

---

### Post by confused57 on 2007-07-05
> **pookerpuff said:**
> that worked now how do i make it a permanent fix?

Open a terminal:
```
cd /boot/grub
sudo cp menu.lst menu.lst_backup
gksudo gedit menu.lst
```

change your root entries to (hd0,x)...also, find the line that begins with #groot, change root to (hd0,x), leave the # in front of groot.

quit & save...this should make your changes permanent.

---

### Post by pookerpuff on 2007-07-05
ok i went through that but when i get to  typing "gksudo gedit menu.lst" then i hit enter and then nothing.what am i doing wrong?

---

### Post by confused57 on 2007-07-05
> **pookerpuff said:**
> ok i went through that but when i get to  typing "gksudo gedit menu.lst" then i hit enter and then nothing.what am i doing wrong?
Just in case you're typing it wrong(it's better to copy & paste), menu.lst is short for menu.list, not menu.first.

---

### Post by pookerpuff on 2007-07-05
no i tried it several times checking the spelling each time and it still produces no results.

---

### Post by confused57 on 2007-07-05
> **pookerpuff said:**
> no i tried it several times checking the spelling each time and it still produces no results.
Sorry, my mistake... you're using Xubuntu...try this:
```
cd /boot/grub
sudo nano menu.lst
```

make your changes(root entries + groot)...Ctrl+X, y, enter...this will save your menu.lst

---

### Post by pookerpuff on 2007-07-05
ok i followed the steps and i ended up with another grub error is it saupposed to be (hd0,x) or (hd0,0)?

---

### Post by confused57 on 2007-07-05
> **pookerpuff said:**
> ok i followed the steps and i ended up with another grub error is it saupposed to be (hd0,x) or (hd0,0)?
It's supposed to be (hd0,0)...I should have mentioned the "x" meant to leave this as is.

---

### Post by pookerpuff on 2007-07-06
ok well now its just being mean,im just gonna download good ole ubuntu and install it instead.thanks for the help

---

### Post by confused57 on 2007-07-06
> **pookerpuff said:**
> ok well now its just being mean,im just gonna download good ole ubuntu and install it instead.thanks for the help
Sorry it didn't work...you should still be able to access your Xubuntu by highlighting your Xubuntu entry, press "e", then change root, then "b" to boot.

You can enter this command from the live cd to see your partitions:
```
sudo fdisk -l
```
-l is a small "L"
this will tell you which is your root partition, in case it's not (hd0,0).

If you do decide to go ahead and install Ubuntu...go into bios and set your USB drive to boot before your internal drive, before you boot the live cd to install...this should automatically set your external hard drive as (hd0) & you "shouldn't" have to perform any "terminal gymnastics" to change your menu.lst...good luck.

---

