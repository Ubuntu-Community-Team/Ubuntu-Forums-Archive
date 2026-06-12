---
title: "having problems formatting 8GB kingston flash drive"
date: 2016-08-27
forum: MINT
---

### Post by Gatorade on 2016-08-27
I was using this flash drive as a live USB to install Ubuntu on a friend's laptop, and somehow it got messed up.
I had a look at it with Gparted, and it says the space is unallocated. 
the device information says partition table : unrecognized 

any attempt to try formatting is blocked because it says unable to mount.

anyone know, how do I fix this, please?

---

### Post by &amp;KyT$0P# on 2016-08-27
How are you trying to format and are you using Gparted to format?
What is the exact error message?

If you don't have a partition table then the disk can't be formatted.  Create a new one if you don't have data you want to recover from the disk.  Use **loop** partition table if you only want one partition and to maximize the use of the storage space on the disk; otherwise use **gpt** (GUID partition table).

---

### Post by Gatorade on 2016-08-30
hi, sorry for the late reply. 
I just tried using Gparted to create the partition table , it didn't work.
I tried loop, and gpt.

I'm not getting an error msg when I use Gparted, it goes through the process, and it looks like its working but nothing happens,and it says 0 operations pending.

ok, I just tried it again using gpt. 
I got an error msg saying Libparted Bug Found , Input/output error during read on /dev/sdb

---

### Post by &amp;KyT$0P# on 2016-08-30
Actually that description sounds like what it'd look like if it worked.  So are you now able to create partition?

---

### Post by Gatorade on 2016-08-30
still can't create the partition.

---

### Post by &amp;KyT$0P# on 2016-08-30
> **Gatorade said:**
> ok, I just tried it again using gpt. 
I got an error msg saying Libparted Bug Found , Input/output error during read on /dev/sdb
Oops, we collided posting.
If you're using Ubuntu 14.04 try [this gparted]("https://launchpad.net/~andykimpe/+archive/ubuntu/gparted")

---

### Post by Gatorade on 2016-08-31
I'm running Mint 17.3 , I just tried updating Gparted , still the same results.

I also have a live USB with Ubuntu 14.04 on it, I wiil update the Gparted on it , and try it again later.

---

### Post by sudodus on 2016-08-31
If there are still problems, I suggest that you try according to this link: [Repair the partition table and file system of a pendrive](http://ubuntuforums.org/showthread.php?t=2196858&p=13409986#post13409986)

> ***Wipe [only] the first megabyte*** to prepare for a fresh partition table without any remaining and confusing data [with mkusb according to this link]("https://help.ubuntu.com/community/mkusb/wipe"). If you wish you can make a partition table and file system too from the wipe menu. Afterwards you can use ***gparted*** to create or modify a partition table with partitions and file systems.

---

### Post by howefield on 2016-08-31
Moved to the "*MINT*" forum.

---

### Post by Dennis N on 2016-08-31
Usually gparted works, but I had one case where gparted refused to create a partition table on flash drive (also Kingston) that had been used with Image Writer (dd).

What worked was to use fdisk to create the partition table:

sudo fdisk /dev/sdb
type 'm' for the menu
type 'd' to delete partitions
type 'o' to create new msdos partition table
type 'w' to write to disk and exit

I was suprised that fdisk could do this and gparted would not. I then was able to use gparted to create a new partition.

---

