---
title: "Gparted not recognizing my partitions correctly"
date: 2012-01-17
forum: Installation &amp; Upgrades
---

### Post by dado_eyad on 2012-01-17
I'm trying to install Ubuntu 11.10 64bit and Gparted not recognizing my partitions correctly.
I read that sometimes there's a problems with HP 4 partitions but they all suggested to delete those partitions and I don't wanna do that.

I just want to shrink a partition and install Ubuntu.
help please.

---

### Post by dino99 on 2012-01-17
HP may have tatooed your hdd, so dont remove the hidden partition(s) made by HP. I prefer to use partedmagic( or at least latest gparted from Sid)

---

### Post by coffeecat on 2012-01-17
@dado_eyad, you appear to be describing two issues. First:

> **dado_eyad said:**
> I read that sometimes there's a problems with HP 4 partitions but they all suggested to delete those partitions and I don't wanna do that.

HP set up their machines with 4 primary partitions. That is the maximum allowed in a MBR partition table. If you want more than 4 partitions, you have to delete one primary partition and replace it with an extended partition in which you can create a number of logical partitions. There is no way around this. So that I don't have to type out all the details again, here is a post I made on this last year:

[http://ubuntuforums.org/showpost.php?p=11270314&postcount=2](http://ubuntuforums.org/showpost.php?p=11270314&postcount=2)

Follow all the links in that and you'll get a reasonable idea of your options. But whatever you do, do **not** let Windows convert your drive to a dynamic drive with dynamic partitions in an attempt to create more than 4 partitions. That is a Microsoft proprietary setup and Linux cannot use it.

> **dado_eyad said:**
> I'm trying to install Ubuntu 11.10 64bit and Gparted not recognizing my partitions correctly.

In what way is Gparted not seeing your partitions correctly? Gparted should have no problem displaying the usual way HP set up their hard drives. Post a screenshot of the Gparted window (Alt + PrintScreen) so that we can see what you mean.

---

### Post by dado_eyad on 2012-01-17
I think I'll delete HP_TOOLS partition.
but I already made more than 4 partitions using windows management tool. I have 5 dynamic partitions and Gparted is mixing them up(attached pics)

I want to shrink C or HD to make a new partition for ubuntu.

---

### Post by darkod on 2012-01-17
> **dado_eyad said:**
> I think I'll delete HP_TOOLS partition.
but I already made more than 4 partitions using windows management tool. I have 5 dynamic partitions and Gparted is mixing them up(attached pics)

I want to shrink C or HD to make a new partition for ubuntu.

You shouldn't have done that. Dynamic partitions (SFS) are MS standard and ubuntu can't install correctly on dynamic disk.

---

### Post by oldfred on 2012-01-17
Windows offical policy on converting back from dynamic is to backup everything, erase drive, repartition and restore/reinstall.

With any third party fixes to partitions make sure you have good backups. 

Best to delete any empty partition you have created if you can, before fixing.

Dynamic volume is a Microsoft proprietary format developed together with Veritas (now acquired by Symantec) for logical volumes.
You can use a third-party tool, such as Partition Wizard MiniTool to convert a convert a dynamic disk to a basic disk without having to delete or format them.
The Partition Wizard software for Windows is supposed to be able to convert dynamic disks to regular partitions without data loss, so it may be what you need to get around this problem; however, I've never used it and so I can't be sure it will work.

Several users have used this, it has a liveCD download to use:
MiniTool Partition Wizard Professional Edition 5.2 to convert without loss of data the disk from dynamic disk to a basic disk.
also used Partition Wizard to set an existing partition logical instead of primary
[http://www.partitionwizard.com/convertpartition/convert-to-basic-disk.html](http://www.partitionwizard.com/convertpartition/convert-to-basic-disk.html)
Converted from dynamic with MiniTool, & repaired windows
[http://ubuntuforums.org/showthread.php?t=1779529](http://ubuntuforums.org/showthread.php?t=1779529)

---

### Post by dado_eyad on 2012-01-17
would it work if I made another partition and installed Ubuntu from windows on that partition?

---

### Post by grahammechanical on 2012-01-17
From what I read in the other posts the answer is no.

First, there are already four primary partitions on the hard disk. One of them has to be deleted and the empty space converted to an extended partition in which you can create several logical partitions.

But you cannot do that because, second, the partitions on your disk are now converted to dynamic partitions by Microsoft Windows. This is a way of fooling the OS that there are more than 4 partitions. Linux operating systems cannot work with Microsoft dynamic partitions.

Linux developers might be able to come up with a way around this if Microsoft were to release information about these dynamic disks but do not hold your breath waiting for Microsoft to do anything to help Linux. Or anyone it see as a competitor.

Of course you could install WUBI in Windows and use that to install Ubuntu inside Windows but it would not really be in its own partition just pretending to be like that. Anyway Wubi is intended for trying out Ubuntu without altering the hard disk. It is not a long term answer.

Regards.

---

### Post by nipunshakya on 2012-01-18
> **dado_eyad said:**
> I think I'll delete HP_TOOLS partition.
but I already made more than 4 partitions using windows management tool. I have 5 dynamic partitions and Gparted is mixing them up(attached pics)

I want to shrink C or HD to make a new partition for ubuntu.

Mate, dynamic partitions, seriously.....they won't let you go with ubuntu.:(Thats the main reason why your gparted showed u an unallocated space instead of another partition.

If you really want ubuntu, there is Wubi. But i won't suggest you go with ubuntu as another big program installed within windows. 

Next way is that you first convert your dynamic partitions to primary partitions. I suggest you do some reading on the following:

[http://www.dynamic-disk.com/resource/simple-volume-to-primary-partition.html](http://www.dynamic-disk.com/resource/simple-volume-to-primary-partition.html)  or,
[http://www.partitionwizard.com/help/convert-dynamic-disk-to-basic-disk.html](http://www.partitionwizard.com/help/convert-dynamic-disk-to-basic-disk.html)
It says that the software won't erase your data when converting from dynamic to primary. I think its worth a try if u want ubuntu in your machine.

In windows seven forums, i found the following worth reading:

[http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk.html](http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk.html)

So you got two choices now. Have a look at both and implement whats best suitable for u.

Goodluck.
Regards,WinuxUser

---

### Post by dado_eyad on 2012-01-25
I used partition wizard 4.2 not the last version or the bootable disk to convert to basic. and it was unbelievably smooth and simple.
thanks everyone.

---

### Post by ottosykora on 2012-01-25
> **dado_eyad said:**
> I used partition wizard 4.2 not the last version or the bootable disk to convert to basic. and it was unbelievably smooth and simple.
thanks everyone.

OK, fine, then you can simply backup somewhere the content of the HP-Tools partition.
Then create an extended and within that you can allocate a small partition for that HP-tools again if you want. 
I did it with all recent HP installs and all works as before.

---

### Post by nipunshakya on 2012-01-26
> **dado_eyad said:**
> I used partition wizard 4.2 not the last version or the bootable disk to convert to basic. and it was unbelievably smooth and simple.
thanks everyone.
Glad it worked. So now you can install ubuntu freely to a space you allocate for it....go on with your installation and let us know if u have a problem...

Happy Linuxing
Regards,WInuxUser

---

### Post by Mark Phelps on 2012-01-26
Now that your partitions have been converted back -- use the Win7 Disk Management tool to shrink the Win7 OS partition to make some room.  You can probably also do this with the Partition Wizard utility.  But do NOT use the Ubuntu installer (with the slider) to do the shrinkage.  That risks corrupting the Win7 OS partition and rendering it unbootable.

---

### Post by dado_eyad on 2012-01-26
thanks guys. I already changed my extra partition to extended and made a partition for Ubuntu and installed it.

---

### Post by Mark Phelps on 2012-01-27
OK then, if everything is working now, please use the Thread Tools at the top of the thread and mark this as SOLVED.  thanks

---

### Post by nipunshakya on 2012-01-27
> **dado_eyad said:**
> thanks guys. I already changed my extra partition to extended and made a partition for Ubuntu and installed it.

Thats great. Glad we could be at your service...Please mark your thread as [SOLVED] using thread tool at top right corner......Happy Linuxing

Regards,WinuxUser

---

