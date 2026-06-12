---
title: "safely erase a hard disk with zeros"
date: 2007-11-08
forum: Installation &amp; Upgrades
---

### Post by eeried on 2007-11-08
Hello,

Someone would like to give a computer but would like us to safely and completely erase the hard disk.

I found this:
> # shred -vfz -n 100 /dev/hda  [http://linuxhelp.blogspot.com/2006/06/how-to-securely-erase-hard-disk-before.html](http://linuxhelp.blogspot.com/2006/06/how-to-securely-erase-hard-disk-before.html)

Someone says in the comments that you would end up melting your HDD. Is this a joke?

How would you go about doing this from Linux (a Live-CD)? I don't want to run any DOS program.

---

### Post by oilchangeguy on 2007-11-08
just format it. the average computer user does not have the knowledge, or tools to recover data once the drive has been formated.

---

### Post by dabl on 2007-11-08
> **eeried said:**
> 

Someone says in the comments that you would end up melting your HDD. Is this a joke?



Yes, along some other baloney in the comments -- but I think the article itself is all good and true.

> 

How would you go about doing this from Linux (a Live-CD)? I don't want to run any DOS program.



That will work (the Live CD) assuming the shred command is in the live system.  Personally, I have an ancient Win 98 bootable floppy diskette, and the only thing I ever use it for is "FDISK", which does about the same thing. 

:)

---

### Post by Daillew on 2007-11-08
Hi eeried, there are lots of ways to safely wipe a drive but the method you choose should really be dependent on the data you want to get rid of. I would imagine the commands shred, wipe and dd are sufficient for most people. Make sure you really want to do this as theres no going back once you have started. I wiped and zeroed my two hard drives when i installed my current dual boot setup without problems. I used the System Rescue CD to prepare my disks for installation, you can get the SRCD from it's home page [HERE]("http://www.sysresccd.org/Main_Page"). The drive can be wiped, partitioned, formatted and prepared for use with the SRCD.

Lets suppose the disk has been used by your friend for storing banking information, personal letters/documents and personal information etc then it's probably better to use a more secure wipe using multiple passes. Darik's Boot and Nuke or "DBAN" is included on the SRCD, from the boot menu enter dban to start it up, You can choose various secure methods of deletion but be warned that some overwrite the disk up to 35 times and on a large disk you are in for very long wait. You can reduce the number of overwriting passes for the given methods but thats really just defeating the object of the program. Check out DBan[ HERE]("http://dban.sourceforge.net/").

My PC is just your average desktop machine used for online shopping, letter writing, emailing, internet, researching interests etc. I don't store any banking or private/confidential information on the machine, that kind of stuff is best stored on removable media. I used the following commands to wipe/zero the disks:

 dd if=/dev/zero of=/dev/hda                  for the first hard drive 
 dd if=/dev/zero of=/dev/hdd                  for the second hard drive

 The first disk is 30 GB and the second disk is 80 GB, i can't remember exactly but it took around 1 1/2 hours to complete overall. DBan can also be set to overwrite the disks with one pass of zeros and takes around the same time. The following command can be used for a similar effect:

 wipe -z /dev/hda

 When the disk is wiped you need to create a new partition table, re-partiton and format  the disk with the scheme that you want/need. [GParted]("http://gparted.sourceforge.net/") is included on the SRCD and is an excellent tool for this purpose.

Have a look at this page "[Secure Deletion Of Data by Peter Gutmann]("http://www.cs.auckland.ac.nz/~pgut001/pubs/secure_del.html")" for information on secure deletion. Later...Daillew

---

### Post by az on 2007-11-08
No, shredding a hundred times will not cause your hard drive to break.  Just think of the drives in a database server which seek and spin almost nonstop for months.

A more useful method would be to use badblocks.  Why not put the work to good use and look for bad blocks at the same time as you are overwriting your data.

sudo badblocks /dev/sda -w -s -p 5

And as to whether it is useful or not is a great question.  Contrary to popular belief, a hard drive is analog.  The data on the platters gets converted to digtial information by the heads and controller.  If you zero the drive, can you recover data from it?

Sometimes.  It depends.  Some low-level tools will be able to pull data from a zeroed disk, while the same tool will come up with nothing on another drive.  Writing random data would be far more effective at scrubbing your drive.  If you are just writing zeros, and you can still pick up bits that were there previously, you don't have to guess what is a new and what is an old bit.

Formatting does nothing.  Even the "low-level" (not quick) format that windows performs does not overwrite a lot of data.  But performing a write test to discover bad blocks does.

If you want to be completely safe, drill a hole through the drive with a 3/8 inch drill bit.  New, big drives are dirt cheap these days anyway.

---

### Post by eeried on 2007-11-09
> drill a hole through the drive with a 3/8 inch drill bit New, big drives are dirt cheap these days anyway.
The problem is new big  HDD aren't compatible with older mobos. I suspect the computer is very old.

```
sudo badblocks /dev/sda -w -s -p 5
```

Many thanks for this useful command. I'll use this.

---

### Post by az on 2007-11-09
> **eeried said:**
> The problem is new big  HDD aren't compatible with older mobos. I suspect the computer is very old.




Actually, it would have to be pretty old - like a 486 or something like that - for an IDE drive to not be recognized.

You can put a 500 gig IDE hard drive in a pentium 1.  And even if the BIOS cannot see more than the first 8 Gigs, it doesn't matter.  You will still be able to boot.  In the unlikely event that this computer is actually that old, you would need to make a /boot partition somewhere in those first few gigs of the drive so that the kernel gets loaded properly.

---

### Post by sh@dowf@x on 2007-11-09
Thanx, SRCD is a godsend.

---

### Post by digitalbenji on 2007-11-09
I'd just use dd for this task, 
```
 dd if=/dev/random of=/dev/sdb
```
you could replace /dev/random with /dev/null to use zeros instead of random dat, and obviously replace /dev/sdb with your hard disk device.  

After doing some research (quickly) onto badblocks, I'm not clear that commands, badblocks -w -s -p 5 will actually remove all data on an entire disk.  badblocks is not designed to format data, rather, it appears to be designed to scan a disk for bad blocks.   Maybe I missed something in the thread though.

---

### Post by psusi on 2007-11-09
You want /dev/zero for all zeroes, and /dev/urandom for random data.  /dev/null can not be read from; it is for output. /dev/random will only return a few bytes, and then block for a while while the system gathers more entropy, so it will take years to generate enough random data to fill the disk.

---

### Post by az on 2007-11-09
> **digitalbenji said:**
> I'd just use dd for this task, 
```
 dd if=/dev/random of=/dev/sdb
```
you could replace /dev/random with /dev/null to use zeros instead of random dat, and obviously replace /dev/sdb with your hard disk device.  

After doing some research (quickly) onto badblocks, I'm not clear that commands, badblocks -w -s -p 5 will actually remove all data on an entire disk.  badblocks is not designed to format data, rather, it appears to be designed to scan a disk for bad blocks.   Maybe I missed something in the thread though.

The -w switch makes it do a destructive write test.  In the same way that dd will fill your drive, badblocks can do it, only it will put the time to better use while it does it.

---

### Post by eeried on 2007-11-11
> Actually, it would have to be pretty old - like a 486 or something like that - for an IDE drive to not be recognized.

You can put a 500 gig IDE hard drive in a pentium 1. And even if the BIOS cannot see more than the first 8 Gigs, it doesn't matter. You will still be able to boot. In the unlikely event that this computer is actually that old, you would need to make a /boot partition somewhere in those first few gigs of the drive so that the kernel gets loaded properly.

Many thanks for the information. It's a pentium but I'll know more next Tuesday. Once you've booted, will Ubuntu see the rest of the HDD and be able to use it?

---

### Post by az on 2007-11-11
It shouldn't be too difficult to use linux on an onld computer.  Just make sure you have enough ram.  256 megs is the minimum for Ubuntu.  You can get away with using a little less by using Xubuntu.

---

### Post by paul382 on 2008-06-13
One more option to erase your hard drive is use of drive wipe softwares which will completely erase hard drive beyond recovery. You can get it lots of [Drive wipe]("http://www.drive-wipe.com") software over internet..

Hope it helps

---

