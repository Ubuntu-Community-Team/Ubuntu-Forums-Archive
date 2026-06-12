---
title: "&quot;No operating system installed&quot; ?"
date: 2009-11-25
forum: Installation &amp; Upgrades
---

### Post by YanickC on 2009-11-25
Hi all, first post.

I had Ubuntu dual-booting with Windows 7 on my laptop up until a month ago, when my laptop was sent for hardware repairs (screen, mouse, webcam problems). They wiped my hard drive, and now I've decided to reinstall Ubuntu 9.10.

I partitioned my hard drive just as before, with one partition for Ubuntu, one for the swap file, one for Windows and one more for my personal data.

But now when I run the installer from the live CD, it tells me that there is no OS installed on my hard drive, and it doesn't see any of my partitions. It only shows that my entire hard drive is empty. But when I restart my laptop without the CD, it boots into Windows as usual. Help!

Here are my specs:

HP Pavilion dv6000
Intel Core Duo CPU
1GB RAM
160GB HDD
OS: Windows 7 32bit

Sorry if this has already been posted and solved. :)

---

### Post by audiomick on 2009-11-25
there is a lot of traffic on this subject. Here's a checklist:
Do the checks to make sure the .iso is good
burn it on a CD-R , not a CD-RW
burn it at the slowest speed possible, preferably 4x

if it is still having trouble, try the "alternate CD" instead of the live cd. The alternate apparently has a different partitioner on it that sometimes works better. It is a text based installer, but nothing to be afraid of.

---

### Post by YanickC on 2009-11-25
Thanks for the suggestion, audiomick.

The live CD I'm using is the official CD I requested to be mailed to me; I didn't download the image from Ubuntu's site. I'll try the "alternate CD" method you mentioned, though. :)

---

### Post by YanickC on 2009-11-26
So I tried to install Ubuntu with Wubi in Windows. The install was successful, but when I restarted my computer and booted into Ubuntu, the installer said "No root directory" or something of the sort. I can't do anything but restart after that point.

I'm still having the initial problem.

EDIT: I rain fdisk -l and it spat this out. Maybe it will help diagnose my problem?

> 
ubuntu@ubuntu:~$ sudo fdisk -l

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe0aa85d4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              13       10320    82785280    7  HPFS/NTFS
/dev/sda3           10320       18674    67107840    7  HPFS/NTFS
/dev/sda4           18674       19458     6292480    f  W95 Ext'd (LBA)
/dev/sda5           18674       19327     5242880    6  FAT16
/dev/sda6           19327       19458     1047552    6  FAT16



---

### Post by darkod on 2009-11-26
If you use the Try Ubuntu option from the CD and run
sudo fdisk -l

what does it says? Any partitions?

---

### Post by YanickC on 2009-11-26
I just posted an edit with the results of fdisk -l. :)

---

### Post by darkod on 2009-11-26
WARNING: GPT

GPT shouldn't be there. It's used for very large drives, over 1TB I think. Google it more.
As you see there are no ext3/ext4 partitions, ubuntu didn't create or format anything it seems. I have no clue how GPT appeared unless it was already there from the repair shop.
I don't have any experience with GPT to help, try googling it little.

---

### Post by YanickC on 2009-11-26
So from what I've read, the only way to get rid of the GPT is to format the hard drive. Is there no other way?

---

### Post by darkod on 2009-11-26
In general, you wouldn't need to remove GPT but in your case it seems somehow corrupted or incomplete. Probably that's why the ubuntu installer doesn't see the partitions, can't read the partition table.
Is windows backup and format an option? Maybe just formatting the windows system partition would help.

---

### Post by darkod on 2009-11-26
You could also try Windows 7 Repair Disc and see if that will remove the GPT by writing the standard MBR on the hdd. If you don't have Windows 7 DVD to do the repair you can get an image of just a repair disc here:
[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)

---

### Post by YanickC on 2009-11-26
Yes, backing up and formatting the HDD is an option. I think it might be the best way to go. Thanks, I will post the results when it is done.

EDIT: Wiping the HDD worked. :)

---

