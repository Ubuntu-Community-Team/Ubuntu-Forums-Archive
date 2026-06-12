---
title: "Run Ubuntu from USB Flash Drive"
date: 2011-10-30
forum: Installation &amp; Upgrades
---

### Post by Zipzit on 2011-10-30
I've got a problem, need some advice.  I'm trying to boot to Ubuntu from the USB flash drive. I want to repeatedly run Ubuntu from flash drive, not install (or merely test drive) Ubuntu from the flash drive...

I'd like the option of booting from a large USB flash drive to run more considerable software.. (Eclipse or netbeans to do java development work, Android Apps, that sort of thing...) I have been all over the links on creating a Live version of Ubuntu on the USB, but that's not exactly what I want.  [https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent)  That web link is tremendously helpful in understand bootable partitions, and in understanding persistence... but...that just gets me to create a 'live' version of an installation CD. (Note: I've Not gotten the persistent thing to work correctly.. some problem is multiple menu config files, or something..)

I'm looking for a 'compiled / executable ' version of Ubuntu to be installed on the USB flash drive.  I'm guessing I will have to trade off storage memory size for speed of boot up.  I know I can place the live version of Oneiric Ocelot 11.10 within 750 MB of storage, but its not clear how much storage is required for a minimum compiled version.  If I had to guess, I'm thinking about 4 gigs or so.

Question #1: how much storage memory is required for Oneric Ocelot base install?

My problem of course is that I want to have my cake and drink beer too.  Windows will only mount the first partition of any removable media, including USB drives.  I'm proposing to partition my 16 GB flash drive 12Gigs of fat32 raw storage, followed by 4 GB of bootable, 'executable' Ubuntu O/S.  I want to be able to run large programs (Eclipse with java tools, say to write Android apps..).  I also want to be able to make a backup copy of source code from the flash drive to other computers easily and quickly.  If I choose, I can use the 12 gigs of flash drive in any windows machine as raw storage.  I know I can have a single partition for all, and the windows machine will see the data, its just cleaner to work with in a dual partition mode.

Question #2: Should I have a dual partitioned storage on a removable drive, or is that just a big waste of time?  

Questions #3: Are there significant advantages to using Oneiric Ocelot over alternative O/S systems for running an integrated development tool?  Is the kernal from Ubuntu better for complicated stuff than the kernal from say... puppy linux ?

Question #3: Anybody been here before with a USB bootable Operating System (with quick launch times)?  

Question #4: Any other comments, hints or tips?

Many thanks in advance,
Zip

---

### Post by haqking on 2011-10-30
> **Zipzit said:**
> I've got a problem, need some advice.  I'm trying to boot to Ubuntu from the USB flash drive. I want to repeatedly run Ubuntu from flash drive, not install (or merely test drive) Ubuntu from the flash drive...

I'd like the option of booting from a large USB flash drive to run more considerable software.. (Eclipse or netbeans to do java development work, Android Apps, that sort of thing...) I have been all over the links on creating a Live version of Ubuntu on the USB, but that's not exactly what I want.  [https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent)  That web link is tremendously helpful in understand bootable partitions, and in understanding persistence... but...that just gets me to create a 'live' version of an installation CD. (Note: I've Not gotten the persistent thing to work correctly.. some problem is multiple menu config files, or something..)

I'm looking for a 'compiled / executable ' version of Ubuntu to be installed on the USB flash drive.  I'm guessing I will have to trade off storage memory size for speed of boot up.  I know I can place the live version of Oneiric Ocelot 11.10 within 750 MB of storage, but its not clear how much storage is required for a minimum compiled version.  If I had to guess, I'm thinking about 4 gigs or so.

Question #1: how much storage memory is required for Oneric Ocelot base install?

My problem of course is that I want to have my cake and drink beer too.  Windows will only mount the first partition of any removable media, including USB drives.  I'm proposing to partition my 16 GB flash drive 12Gigs of fat32 raw storage, followed by 4 GB of bootable, 'executable' Ubuntu O/S.  I want to be able to run large programs (Eclipse with java tools, say to write Android apps..).  I also want to be able to make a backup copy of source code from the flash drive to other computers easily and quickly.  If I choose, I can use the 12 gigs of flash drive in any windows machine as raw storage.  I know I can have a single partition for all, and the windows machine will see the data, its just cleaner to work with in a dual partition mode.

Question #2: Should I have a dual partitioned storage on a removable drive, or is that just a big waste of time?  

Questions #3: Are there significant advantages to using Oneiric Ocelot over alternative O/S systems for running an integrated development tool?  Is the kernal from Ubuntu better for complicated stuff than the kernal from say... puppy linux ?

Question #3: Anybody been here before with a USB bootable Operating System (with quick launch times)?  

Question #4: Any other comments, hints or tips?

Many thanks in advance,
Zip

Use Unetbootin or Startupdisk creator.

Check the box for use persistence and choose the size you want.

If its a 16GB or 32 Gb say, choose whatever you want for persistance or use gparted to create a sepearate partition.

I run many Ubuntu version from USB, including a 11.10 with Unity 3D and desktop cube from a 2GB

or just boot to a Live CD and choose install and choose the USB as the destination

---

### Post by oldfred on 2011-10-30
Pros & cons of persistent install over direct install to flashdrives 
[http://ubuntuforums.org/showthread.php?t=1655412](http://ubuntuforums.org/showthread.php?t=1655412)

I think a full install now requires 4.4GB. Flash will not be particularly fast but is functional. I would not use it for major development though. I have a 16GB flash with my install in 8GB and 8GB for data. But I used gpt (more to learn about gpt) and have an ext4 data partition. Gpt is recommended for SSDs if not installing Windows and I figured my flash was a poor man's SSD. Similar settings, just not as fast.

HOW TO Avoid Wubi & Install Ubuntu on USB Drive -amjjawad
[http://ubuntuforums.org/showthread.php?t=1650699](http://ubuntuforums.org/showthread.php?t=1650699)

It really is just like any install to a second drive, you have to use manual install so you can choose to install the grub2 boot loader to the MBR of the flash drive. And you may want to make some settings to reduce writes to add a bit of speed.

It does not have to be encrypted BIOS based system:
Standard full install with screenshots to flash or SSD:
Ubuntu Encrypted Flash Memory  Installation
[http://members.iinet.net/~herman546/p19.html](http://members.iinet.net/~herman546/p19.html)
More discussion Dec 2010, more SSD info
[http://ubuntuforums.org/showthread.php?t=1643591](http://ubuntuforums.org/showthread.php?t=1643591)

Use ext2 or ext4 without journal:
sudo tune2fs -O ^has_journal /dev/sda1
sudo tune2fs -o discard /dev/sda1
No swap or set swapiness or install 'Dynamic Swap Space Manager' from the Ubuntu Software Center
After installing, change the fstab so that everything gets mounted with noatime.
change to noop i/o scheduler

You want journal to speed up system recovery if you have to do repairs or run fsck. But if partition is small then it does not take long to fsck anyway and without journal writing is reduced.
SSD’s, Journaling, and noatime/relatime 
[http://thunk.org/tytso/blog/2009/03/01/ssds-journaling-and-noatimerelatime/](http://thunk.org/tytso/blog/2009/03/01/ssds-journaling-and-noatimerelatime/)
noatime,nodiratime options in fstab to make the ssd last longer when using a ext4 partition

---

### Post by Zipzit on 2011-11-01
Good news.. I was totally able to install Ubuntu 11.10 on my flash drive. Had to use one partition.  Works good, loads fast, but there are other major problems associated with it.

Bad news...  Aaaargh!!!

1) Because I was only able to partion the USB drive in Ext2 to run Ubuntu, that drive is no longer visible when plugged into a windows machine (for transfering small files.)  Not sure why the load wouldn't accept the two partion thing.. my intent was for a small partition (say 2GB in FAT32) and 14GB in EXT2 with boot flag.  I was not happy with the live CD partition tool.. very clumsy for this task.  (and yes, I don't understand all the details in the back end, and that sets me up for issues..)

2) The worst, very worst thing is now I've corrupted the windows hard drive on my laptop.  I would have thought when I installed the O/S to the 16GB Flash drive, using another 2GB flash drive with the live install on it (via unetbootin) that it would have absolutely left the hard drive alone.  No such luck. Somehow my master boot record has been corrupted.  I'm in a panic mode over the data in my documents on the windows drive.  I can't get to that data anyhow that I can figure out.

Original error message (when trying to boot to hard disc, without USB plugged in...) = Error: No such device 85a5f9ee-....   grub rescue>

I've discovered the forum posting: [http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)     I've downloaded the grub repair tool via [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Using that tool has poured gasoline on my burning laptop.  Now I've got four different boot choices, non of which get me back to my windows XP Pro hard drive. (two are related to the USB Ubuntu drive, two are hardware testers)  I can't even see the boot partition for windows anymore.  To make matters worse, this is a work computer, with corporate IT guys overlooking everything.  Ugh. Oh. and they don't give us users admin rights, so you can figure this will get ugly quickly..  I've thought of telling them I accidently ran over the laptop with my car (ha!)

One thing that gives me a little bit of hope:  When I run ubuntu disk utility, I can mount the 160GB hard drive.  I can see the dev/sda.. Partitioning = Master Boot Record, disk is healthy.  Volumes: WinPE116, 526MB Fat, followed by Unknown 160 GB device /dev/sda2  (When I mount the disk, I can see the 526MB partition, but not the 160GB NTFS partition.

the good news is most of my important work stuff is on the shared drive. There are a few things on the local hard drive I'd sure love to save.  Any ideas on how to proceed (and yeah I can go to the IT guys, where they will squeeze my acorns in a vise...)    Hmmm... maybe the IT guys can boot to windows, and we can look at the hidden drive.  I certainly don't have an XP boot disk. 

Any advice to give on how to re-inflate flattened acorns?

thanks, 
zip

---

### Post by oldfred on 2011-11-01
Did you miss this?
> It really is just like any install to a second drive, you have to use  manual install so you can choose to install the grub2 boot loader to the  MBR of the flash drive. 
You need to reinstall a Windows boot loader to the internal drive and install grub2's boot loader to the flash drive. You do have to pay attention to which drive is sda, sdb as some systems promote a flash drive to sda, others may mount it as sdd or some other place.

So many users did the same as you that the author of the boot script posted these instructions:
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Computer_does_not_boot_without_external_drive](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Computer_does_not_boot_without_external_drive)

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10) - talsemgeest
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
Reinstall grub2 - Short version & full chroot version
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2)

The installer partition tools is limited as it is intended to just install Linux. If you want windows partitions you need to use gparted and partition in advance, then you can have the first partition as NTFS or FAT32. If partition is small FAT32 is ok.

---

### Post by Zipzit on 2011-11-01
Yeah, I was able to rebuild the master boot record using boot repair, but I work for a very LARGE company.. the boot records are bizzare, and not a simple setup that a normal user would see.  The other thing they do is utilize a super secure file system (NTFS / blended with something else..) They want to be doggone sure that if a laptop gets lost NOBODY will be able to acess the data on the hard drive.  Users don't have admin rights. After I did the MBR rebuild, the laptop would start to boot into windows, then fail at a Blue Screen of Death. 

So I had to go thru the acorn and vise exercise.  I ended up buying the IT guy lunch today.  Lost the data on the local hard drive, but there wasn't too much stored there.  I've been burnt before, use online data storage for all business work.  

I do wish I had realized that the Ubuntu install was trying to even access the laptop's hard drive.  (Hint.. I wish there was a custom option at the live CD to install the info to SSD or to USB flash drive... one that took extra care in avoiding a hard drive..)

Oh well, life goes on.  OldFred, I haven't yet tried your suggestions.. I'm nervous about doing setup stuff on the company laptop anymore.  I'll have to wait till I get home and do that using my own Linux computer where I have full control of issues.  


thanks to all for your replies..
zip.

---

### Post by fresnofred on 2011-11-18
i disconnect hard drive, boot to live cd, and do a regular install.  It will find the flash drive and do a regular install to it.  don't forget to reconnect hard drive after u are finished and before rebooting.

---

