---
title: "Re: No root file system is defined -What is the workaround"
date: 2010-03-11
forum: Installation &amp; Upgrades
---

### Post by drashok on 2010-03-11
[SIZE="1"][/SIZE]Hi Ubuntu lovers,

I get the message 
> "[B]No root file system is defined.
Please correct this from the partioning menu[/B]."

This is during _installing Ubuntu 9.04 Desktop _Edition on _separate windows XP partition _D drive 19GB. I can't go further.

I have seen the following threads with no solution in view. 

[HTML]http://ubuntuforums.org/showthread.php?p=2239969
http://ubuntuforums.org/showthread.php?t=1377605&highlight=no+root+file+system+is+defined
http://ubuntuforums.org/showthread.php?t=922331&page=2
[B]ctrl+alt+f3 
installationslog.zip[/B]
http://ubuntuforums.org/showpost.php?p=5731340&postcount=7 done 
I have searched in 'check if already posted,' and I did not see solved results.
[For run live CD and click on install - not applicable]
http://fs-driver.org/download.html[/HTML]

**_Kindly tell me what exactly must I do _**so that I can have dual boot.
I am sure of getting quick assistance.

Regards,
Dr. Ashok Koparday
[SIZE="1"]
(I had posted, I guess, in the wrong forum, which was Dell Ubuntu forum. I had posted as a reply instead of a new thread. The thread was [http://ubuntuforums.org/showthread.php?p=8915429#post8915429](http://ubuntuforums.org/showthread.php?p=8915429#post8915429))[/SIZE]

---

### Post by psusi on 2010-03-11
You have to define a root file system.  A screen shot or explanation of the partitions you tried to set up would be helpful.

---

### Post by oldos2er on 2010-03-11
The root file system is usually defined as "/" (without quote marks).

---

### Post by drashok on 2010-03-14
[B]Thanks Psusi,
Thanks oldos2er/Ann,[/B]

> A screen shot or explanation of the partitions 
**Please Note:** There is no question of partition.
This error message is during 
**"Installing withing windows XP without repartitioning on a separate drive."** 

I am sure you can guide better.

Regards,
Dr. Ashok Koparday

---

### Post by drashok on 2010-03-14
How to install?

---

### Post by efflandt on 2010-03-14
Most of us have no experience with Wubi because we install Linux to its own partition(s) instead of within Windows.

But someone who does know Wubi may need to know what drive D really is.  Is it a partition on your primary drive or another drive, and is it a primary or logical partition?

If you can boot an Ubuntu install CD to a live system, post the output of **sudo fdisk -l** (small L) and point out which partition is D.

---

### Post by drashok on 2010-03-18
Hi,
Thanks efflandt,

Windows XP has drive/partitions C D E F.

**After i have used WUBI to load Ubuntu in Windows XP it starts to install. Then it hits this error message** "No root file system is defined, please correct this from the partitioning menu." 

[B]There is no option on the screen. No where to click.
The only thing that I can do to get out of this is to shut down the computer. [/B]
Kindly show how to installing Ubuntu in Windows XP without the error message.

Regards,
Dr. Ashok Koparday

---

### Post by psusi on 2010-03-18
Don't use WUBI?  I've never tried using it myself so I can't help with wubi specific problems.  Most people use a normal install, not wubi.

---

### Post by allxk on 2010-10-13
** Installing Ubuntu 10.10 64-bit**                                                                             This is a bug!
Please see attached image:
The disk partitioned with gparted.
Ubuntu 10.10 x64 Installation window will not show any partitions, and edit partition option.
Same thing with Ubuntu 10.10 x32.
Will somebody report it to developers?

---

### Post by CYD on 2010-10-14
I got the same thing!
SATA Hard drive, SDA1 is EXT3, used. No matter how I partition or configure the remaining unused space, I cannot change the dropdown from SDA.

Bootable USB Jumpdrive created in Ubuntu from .iso image pulled from the alternate torrent download.  Liekwise, I have tried both the 64 and 32 bit variants, same result as previous post.

~CYD

---

### Post by psusi on 2010-10-15
> **allxk said:**
> ** Installing Ubuntu 10.10 64-bit**                                                                             This is a bug!
Please see attached image:
The disk partitioned with gparted.
Ubuntu 10.10 x64 Installation window will not show any partitions, and edit partition option.
Same thing with Ubuntu 10.10 x32.
Will somebody report it to developers?

I'm not sure why you decided to post that in this very old thread, but you should open a terminal and run sudo dmraid -s.  If it says it finds any raid arrays, then you are trying to use a disk that was once part of a bios fake raid, and still says it is, which is why the installer does not show it as a viable disk.

---

### Post by Devon Fletcher on 2010-12-21
1. boot Ubuntu from CD (or USB stick)
2. run Gparted (System>Administration>Partition Editor), to set up the Ubuntu Partition. I formatted the partition as ext4, this may not be essential.
3. run Disk Utility, select the HD, then the partition (click on the appropriate rectangle in 'Volumes').
4. click 'Edit Filesystem Label' and type "/" (without quotes) in the 'Choose a new filesystem label' dialogue box. click 'Apply'.
5 double-click the 
Install Ubuntu' icon, away she goes!


Devon

PS thanks to Ann for the cryptic clue, I'd never have got there without!

---

