---
title: "Is installing on HD the only way?"
date: 2011-04-18
forum: Installation &amp; Upgrades
---

### Post by Flik Shen on 2011-04-18
Hi guys,
 
I have 8GB usb pen drive and wanna install a persistent ubuntu 10.10 on it form Live CD.
However, I always ran out of space even I extended the loop casper-rw file 2GB.
 
It did NOT work for me simply delete casper-rw loop file and create an more than 5GB partition labeled casper-rw. Indeed usb pen could not boot up anymore after I did that.
 
Then I think maybe I could run installer and make a complete installation on usb pen driver. Unfortunatively it stopped with I/O error. I tried this both on SanDisk and no brand usb pen. (I think it should not work even after successful installation due mutable device name when plug into different port.)
 
I search the google and got a topic about Customize Live CD. (Why default ubuntu Live USB does not server my demand? Since I use Dell Latitue E4310 and my wireless card driver is not included in default installation.) Following the guideline, I rsync whole Live CD on HD which is ntfs partition except file filesystem.squashfs under casper sub-directory. Then I unsquash squashfs file system into another temp directory (also ntfs partition). When I try to chroot to jail the changes I might do, I was occurred by an error again. It said "Cannot execute '/bin/bash':  Permission Denied". When I look into the uncompress the directory and found the permission is 600 (-rw-------) and I tried command chown and chmod but could not change the permission.
I also tried to uncompress squash file system to ext3/ext4 partition on usb pen drive and same issue.
 
I have tried such many ways.
Is there any step I missed or thought it in wrong way?
Does it mean above operations are too difficult to usb pen drive and a HD installation is required?
 
Any suggestion and ideas are welcome.
 
thanks a lot.

---

### Post by Hedgehog1 on 2011-04-18
If you hardware allows you to disconnect the hard drive, you can install off the LiveCD onto the USB as the hard drive.

I have several of these '**Ubuntu-On-A-Stick**!' USB sticks.  They work well - but the faster the USB stick is, the better.

You can also do a manual install and add an FAT32 partition to the USB stick so you can still use it to move files from one windows PC to another:

[IMG]http://img197.imageshack.us/img197/6631/gparteduaos.png[/IMG]

***The Hedge***

:KS

p.s. I have ddresuce and gparted loaded on mine, so I can use it to rescue PC's where windows is crashed/infected, or move one hard drive's data to another.

---

### Post by oldfred on 2011-04-19
A full install to a flash drive is just like any install to a second drive, but you may want to change a few settings to reduce writes for life & speed.

Step by Step Full install 8GB C.S.Cameron Post #7
[http://ubuntuforums.org/showthread.php?t=1719346](http://ubuntuforums.org/showthread.php?t=1719346)

It does not have to be encrypted:
Standard full install with screenshots to flash or SSD:
Ubuntu Encrypted Flash Memory  Installation
[http://members.iinet.net/~herman546/p19.html](http://members.iinet.net/~herman546/p19.html)
More discussion Dec 2010, more SSD info
[http://ubuntuforums.org/showthread.php?t=1643591](http://ubuntuforums.org/showthread.php?t=1643591)

Use ext2 or ext4 without journal:
tune2fs -O ^has_journal /dev/sda1
No swap or set swapiness
After installing, change the fstab so that everything gets mounted with noatime.
change to noop i/o scheduler

You want journal to speed up system recovery if you have to do repairs or run fsck. But if partition is small then it does not take long to fsck anyway and without journal writing is reduced.
SSD’s, Journaling, and noatime/relatime 
[http://thunk.org/tytso/blog/2009/03/01/ssds-journaling-and-noatimerelatime/](http://thunk.org/tytso/blog/2009/03/01/ssds-journaling-and-noatimerelatime/)
[https://wiki.archlinux.org/index.php/Solid_State_Drives](https://wiki.archlinux.org/index.php/Solid_State_Drives)

---

### Post by Flik Shen on 2011-04-19
> **Hedgehog1 said:**
> If you hardware allows you to disconnect the hard drive, you can install off the LiveCD onto the USB as the hard drive.
 
I have several of these '**Ubuntu-On-A-Stick**!' USB sticks. They work well - but the faster the USB stick is, the better.
 
You can also do a manual install and add an FAT32 partition to the USB stick so you can still use it to move files from one windows PC to another:
 
[IMG]http://img197.imageshack.us/img197/6631/gparteduaos.png[/IMG]
 
***The Hedge***
 
:KS
 
p.s. I have ddresuce and gparted loaded on mine, so I can use it to rescue PC's where windows is crashed/infected, or move one hard drive's data to another.
 
If I could choose a usb pen during installation setting, is Disconnect HD still necessary?
Did you do installation as attached screenshot to choose usb as the target disk?
 
How fast the usb pen drive is expected? Since installation will be interrupted by an error as attached error snapshot.
 
Did I do something wrong?
 
p.s. I boot from Live CD.

---

### Post by Flik Shen on 2011-04-19
> **oldfred said:**
> A full install to a flash drive is just like any install to a second drive, but you may want to change a few settings to reduce writes for life & speed.

Step by Step Full install 8GB C.S.Cameron Post #7
[http://ubuntuforums.org/showthread.php?t=1719346](http://ubuntuforums.org/showthread.php?t=1719346)

It does not have to be encrypted:
Standard full install with screenshots to flash or SSD:
Ubuntu Encrypted Flash Memory  Installation
[http://members.iinet.net/~herman546/p19.html](http://members.iinet.net/~herman546/p19.html)
More discussion Dec 2010, more SSD info
[http://ubuntuforums.org/showthread.php?t=1643591](http://ubuntuforums.org/showthread.php?t=1643591)

Use ext2 or ext4 without journal:
tune2fs -O ^has_journal /dev/sda1
No swap or set swapiness
After installing, change the fstab so that everything gets mounted with noatime.
change to noop i/o scheduler

You want journal to speed up system recovery if you have to do repairs or run fsck. But if partition is small then it does not take long to fsck anyway and without journal writing is reduced.
SSD’s, Journaling, and noatime/relatime 
[http://thunk.org/tytso/blog/2009/03/01/ssds-journaling-and-noatimerelatime/](http://thunk.org/tytso/blog/2009/03/01/ssds-journaling-and-noatimerelatime/)
[https://wiki.archlinux.org/index.php/Solid_State_Drives](https://wiki.archlinux.org/index.php/Solid_State_Drives)
Where should I install the boot loader?
/dev/sdb or /dev/sdb1?

---

### Post by oldfred on 2011-04-19
Did you check mdsum, and burn at the slowest speed your writer allows?

USB flash is slower than hard drive both due to USB port and flash not as fast. For me it is functional for occasional use. Writes are slow, so you do want to minimize those. It took me at least twice as long to install as that was a lot of writing.

You want to install grub2's boot loader to the MBR of the flash drive. If the drive is sdb the that would be correct. Do not install to a partition like sdb1 as then it will not be bootable.

---

### Post by wilee-nilee on 2011-04-19
see last post.

---

### Post by Hedgehog1 on 2011-04-19
* Deleted - **oldfred** had answered the question and I missed that fact on the first read.

---

### Post by Flik Shen on 2011-04-22
Eventually, Ubuntu is running on USB pen.
I re-burn a low speed disk and use that disk i could install 10.10 successfully.
I am sure about whether partitioning also help or not.

Any thanks everybody's help.

---

