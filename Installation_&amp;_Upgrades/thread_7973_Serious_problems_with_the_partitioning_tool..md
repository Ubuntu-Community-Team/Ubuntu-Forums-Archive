---
title: "Serious problems with the partitioning tool."
date: 2004-12-13
forum: Installation &amp; Upgrades
---

### Post by FeliceMente on 2004-12-13
I installed Ubuntu 4.10 for the second time.
The first time using normal installation, and... I got my primary Windows XP partition totally corrupted. I thought it was grub's fault, and so I reinstalled Ubuntu, after recovering someway the lost data, this time using expert installation, so I could choose lilo.

Well... I had problems this time, too!
I lost one of the logical NTFS partitions contained in the same extended partition when Ubuntu was installed, and the previous was was corrupted (the BRs were no more correct, because two partitions overlapped). I could fortunately make everything work well again eliminating the ReiserFS and wap logical partitions I had created for Ubuntu, and manually changed the boundaries of the "corrupted" NTFS partitions using Ranish Partition Manager).

I defenitely think Ubuntu installer ha a serious problem with the partitioning tool (I've used Linux and othe OSs (even BeOS, QNX, FreeBSD, etc..) for years, without NEVER having problems with the existing partitions, and this is the first time i happens).

---

### Post by p!=f on 2004-12-13
The default Ubuntu kernel has no NTFS write support so I doubt it could damage the partition by accessing it. 
Did you partition the disk yourself or you let the installer to do it automatically? Did you set up mount points for the NTFS partitions?

* MODs, please move the thread to appropriate forum. *

---

### Post by TravisNewman on 2004-12-13
[QUOTE=p!=f]The default Ubuntu kernel has no NTFS write support so I doubt it could damage the partition by accessing it. 
Did you partition the disk yourself or you let the installer to do it automatically? Did you set up mount points for the NTFS partitions?

* MODs, please move the thread to appropriate forum. *[/QUOTE]
 Also, did you do any resizing of ntfs partitions with the Ubuntu install cd? That's a sure fire way to mess stuff up

---

### Post by FeliceMente on 2004-12-13
[QUOTE=p!=f]The default Ubuntu kernel has no NTFS write support so I doubt it could damage the partition by accessing it. [/QUOTE]
But the partitioning tools during installation caould have done it...


> Did you partition the disk yourself or you let the installer to do it automatically? Did you set up mount points for the NTFS partitions?
The first time I used default installation and manually partitioned the HD (I actually used the already present swap partition and changed the already present ext3 partition into ReiserFS), and didn't choose any mount point for the other partitions.

I had one NTFS primary partition, and one extended, with 2 logical NTFS, + swap + reiserfs.

I got the primary one corrupted (with no way of manually correct it: I had to use a softare for recovering data from NTFS partitions).


In the second case, I used expert instalation (and choose lilo, because I had previously had problems with grub, also with Fedora).
I used the already present swap partition, removed the previous ReiserFS partition, and recreated.

I set the mount point for a FAT32 partition present on a different disk, and could not set mount points for the NTFS partitions present on the disk where ubuntu was installed.

I got the NTFS partition near (before, in the disk) destroyed, and the one before this one with uncorrect start-end values (and had to use Ranish Partition Manager for manually set the righ ones).

I'm 100 % I didn't do any error in neither case (and I never did in years....).


PS. I think the forum about security isn't wrong, considering I lost important data in both cases... It's not just an installation problem I' have.... I think you should star considering the possibility of having some problem in the installer...

---

### Post by FeliceMente on 2004-12-13
[QUOTE=panickedthumb]Also, did you do any resizing of ntfs partitions with the Ubuntu install cd? That's a sure fire way to mess stuff up[/QUOTE]
Nope. I NEVER resize partitions, (not even using PartitionMagic, etc...).

---

### Post by p!=f on 2004-12-14
My excuses if I offended you in my previous post. Just wondering how could that happen. I have almost the same setup as you have. 3 NTFS partitions. I installed Ubuntu twice (I had to repartition second time )...
I admitt it could be a bug in the installer. In that case it would be good to hunt it down. :)

Could you reproduce it without losing valuable datas?

---

### Post by FeliceMente on 2004-12-14
[QUOTE=p!=f]My excuses if I offended you in my previous post. Just wondering how could that happen. I have almost the same setup as you have. 3 NTFS partitions. I installed Ubuntu twice (I had to repartition second time )...
I admitt it could be a bug in the installer. In that case it would be good to hunt it down. :)

Could you reproduce it without losing valuable datas?[/QUOTE]
You didn't offend me. I'm sorry if I looked offended or angry in my post. I didn't mean to be! :-P

Anyway... I reinstalled it for the third time yesterday evening, without creating/deleting partition, but only using the swap partition already present, and simply reformatting the ReiserFS linux partition previously created to ext3 (just for cleaning it), and also set a mount point for a fat32 partition present on another disk, and everything seems to work weell so far. I rechecked the partitions, and here are no errors this time.

So... If there's really any bug, it is just when deleting/creating partitions, not also when formatting or using a previously formatted area.


I can't unfortunately make tests now, 'cause I have important data on the other partitions, but will try to do some tests as soon as possible on a different machine (if this can help...)! :-P

---

### Post by Vitriol7288 on 2007-05-15
> **FeliceMente said:**
> Nope. I NEVER resize partitions, (not even using PartitionMagic, etc...).


[food science Paris Hilton Tsunami solar Credit Cards](http://oldcda.design.ucla.edu/~kpasko/watercolor/css/ph/forced-porn.html)

---

