---
title: "[SOLVED] Gutsy on two disk in one box"
date: 2007-11-09
forum: Installation &amp; Upgrades
---

### Post by Mark_in_Hollywood on 2007-11-09
I have two hard disks in this box. I want Gutsy on both. The LiveCD wanted to use the /sdb (pri. slave) FIRST. I guess I don't care which drive is master or slave, but how do I do the install?

---

### Post by RTrev on 2007-11-09
> **Mark_in_Hollywood said:**
> I have two hard disks in this box. I want Gutsy on both. The LiveCD wanted to use the /sdb (pri. slave) FIRST. I guess I don't care which drive is master or slave, but how do I do the install?

I'm not entirely clear what you're trying to do.  Do you want Gutsy to be running in a RAID array composed of your two disks?  If so, I believe you need to use the "Alternate" CD, which is not a "Live" CD but rather just a text installation routine.  It has the added functionality in the partitioning section to let you set things up as RAID, LVM, etc.

HTH,
Bob

---

### Post by Mark_in_Hollywood on 2007-11-10
Both hard disks are to have Gutsy installed. No RAID. 

Currenty, 40gig is pri. slave and 20gig is pri. master.

20 gig is having Campcaster radio and music only, ie, no gimp, no OpenOffice, a minimal use of diskspace and docs, webpages and be moved from smaller harddrive to larger.

40 gig is "regular"  Gutsy with Gimp, Firefox and all "bells & whistles".

Esentially 2 separate OSs on 2 harddrives, able to "see" each other each disk for a different purpose.

---

### Post by RTrev on 2007-11-10
> **Mark_in_Hollywood said:**
> Both hard disks are to have Gutsy installed. No RAID. 

Currenty, 40gig is pri. slave and 20gig is pri. master.

20 gig is having Campcaster radio and music only, ie, no gimp, no OpenOffice, a minimal use of diskspace and docs, webpages and be moved from smaller harddrive to larger.

40 gig is "regular"  Gutsy with Gimp, Firefox and all "bells & whistles".

Esentially 2 separate OSs on 2 harddrives, able to "see" each other each disk for a different purpose.

Well, that should be easy to do.  Just modify each installs fstab so that the other disk gets mounted as a data disk.

But, I'm puzzled.  Why not install everything you need in the way of applications of the little disk, and use the larger disk exclusively for your data?  Why have two operating systems?

Sorry.. I'm feeling a bit dense today.  :)

---

### Post by Mark_in_Hollywood on 2007-11-10
The radio station disk will eventually move to another box.

---

### Post by RTrev on 2007-11-10
> **Mark_in_Hollywood said:**
> The radio station disk will eventually move to another box.

Ahah.  Okay, I guess fstab would be the way to go for this, unless someone has a better idea?

Are you familiar with editing the /etc/fstab text file?

---

### Post by Mark_in_Hollywood on 2007-11-10
"Well, that should be easy to do. Just modify each installs fstab so that the other disk gets mounted as a data disk."

I'm not communicating.

How do I use the Ubuntu Gutsy "desktop" installation CD to install gutsy on the pri. slave?

then how do I make the two disks "see" each other.

---

### Post by RTrev on 2007-11-10
> **Mark_in_Hollywood said:**
> "Well, that should be easy to do. Just modify each installs fstab so that the other disk gets mounted as a data disk."

I'm not communicating.

How do I use the Ubuntu Gutsy "desktop" installation CD to install gutsy on the pri. slave?

then how do I make the two disks "see" each other.

Does the Master disk show up as a different drive than the slave disk while you're doing your install?  If not, then you might have to remove one disk, install, insert the other disk, install.

But if during the install you can see both disks, just pick the one you want.  Maybe I'm missing something here.

To make the two disks "see" each other, again we need to edit the /etc/fstab file.

For example, my boot disk is a little 74G Raptor.  Once the install is done, I open a terminal and issue the command:

```
vol_id /dev/md1
```

Having that volume ID, I then add my (in this case a RAID array) to fstab so it looks like this:

```

#/dev/md0
UUID=33f2638c-f8da-4494-8337-be8b5d11f34e  /home/bob/Data1  ext3  defaults,data=writeback,noatime,nodiratime  0 2

```

Once that's there, then the disk will be automatically mounted on boot.  I can also force a mount immediately by using:

```
sudo mount -a
```

So what I did was create a directory called /home/bob/Data1 and use that for the mount point for the RAID array I wanted access to.  In your case it probably wouldn't be a RAID array, so you'd just get the volume id of the *other* drive, and stick it in there so it's mounted on each boot.

Then, booting from the other disk, you'd do the same thing, so that you have access to both disks no matter which disk you boot from.

Are we on the same page?

Bob

---

### Post by Mark_in_Hollywood on 2007-11-10
Doh! (that's for me)

I guess you are saying that I can insert the (in my case) Gutsy Alternate Desktop CD and when the screen comes up that asks where to install, you say (again in my case) **sdb**? That's it? I would have expected simple & easy, but do to newbie-doh! factor, I must double check. Thanks, again, Bob.

---

### Post by RTrev on 2007-11-10
> **Mark_in_Hollywood said:**
> Doh! (that's for me)

I guess you are saying that I can insert the (in my case) Gutsy Alternate Desktop CD and when the screen comes up that asks where to install, you say (again in my case) **sdb**? That's it? I would have expected simple & easy, but do to newbie-doh! factor, I must double check. Thanks, again, Bob.

Sure, I have an sda and an sdb also, and I have different installs on each.  When GRUB comes up, I can choose which to boot to.  Since you already have an install on sda, when you install to sdb it will say "Hey, you've got another install out on sda."  Just allow it to go ahead and install as it wants, and you'll be able to access either system at boot.

Hope this helps!

Bob

---

### Post by Mark_in_Hollywood on 2007-11-10
Ya' lost me.

"When Grub comes up"?

I was avoiding talking about this thinking to simplify, but I've failed.

Some time ago, putting a windows disk as pri/slave blew grub up on the 40gig. I tried SuperGrub and all kinds of things and have reconciled myself to a reinstall. The /home is safe on the 20gig and now all I want to do is install Gutsy over the 40 gig, which was Dapper.

---

### Post by RTrev on 2007-11-10
> **Mark_in_Hollywood said:**
> Ya' lost me.

"When Grub comes up"?

I was avoiding talking about this thinking to simplify, but I've failed.

Some time ago, putting a windows disk as pri/slave blew grub up on the 40gig. I tried SuperGrub and all kinds of things and have reconciled myself to a reinstall. The /home is safe on the 20gig and now all I want to do is install Gutsy over the 40 gig, which was Dapper.

Ah, the problem may be that you haven't seen "GRUB come up."  :)

When there is only a single OS installed, you don't see GRUB except for a little line saying it will boot in 2 seconds or something like that.  But when there are multiple OS's, then GRUP pops up a menu to let you choose which one you want to boot into.

In your case, GRUB will list your sdb install on top, and if you want your sda install you'll arrow down to it.  

I've done this lots of times, because with two boot disks I can easily try out other distros without hosing my main one, and without having to mess with partitioning.  

Both of my disks are on their own SATA channel with none of the master/slave stuff (are we still allowed to call it that, or is it now considered politically incorrect?)

So anyway, once you've completed the install, the next boot will present you with a GRUB menu you may not have seen before.. and that's what I meant by "when GRUB comes up."

Sorry for not being more clear.

---

### Post by Mark_in_Hollywood on 2007-11-10
My GRUB already has more than 1 kernel to boot from, but it shows no sdb, at least not on the boot time screens. 

Here is my /boot/grub/menu.lst


title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=0fe55993-b869-4a83-9c32-f17d4617bb3c ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=0fe55993-b869-4a83-9c32-f17d4617bb3c ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, kernel 2.6.22-7-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-7-generic root=UUID=0fe55993-b869-4a83-9c32-f17d4617bb3c ro quiet splash
initrd		/boot/initrd.img-2.6.22-7-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-7-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-7-generic root=UUID=0fe55993-b869-4a83-9c32-f17d4617bb3c ro single
initrd		/boot/initrd.img-2.6.22-7-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb1.
title		Ubuntu, memtest86+ (on /dev/sda1) (on /dev/sdb1)
root		(hd1,0)
kernel		/boot/memtest86+.bin  
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb1.
title		Ubuntu, memtest86+ (on /dev/hdb1) (on /dev/sdb1)
root		(hd1,0)
kernel		/boot/memtest86+.bin  
savedefault
boot

GRUB does NOT offer to boot to the "other" drive.

---

### Post by RTrev on 2007-11-10
Hmm.  It won't show you other *kernels* on the same disk, but it should show you other installs on *other* disks.  I don't see anything on another disk except memtest.

I think I had better step back and let someone more knowledgable take over.  I thought we had an easy problem to solve here, but it's looking like I'm not doing a very good job of solving it.

Anybody?  Step in and clear this up for all of us?

---

### Post by RTrev on 2007-11-11
Maybe this will help.. this is what my own GRUB /boot/grub/menu.lst looks like, with the top stuff trimmed off:

```

## ## End Default Options ##

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=c4d7e1f3-2ec8-4ac0-86bd-b30499d8e9ed ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=c4d7e1f3-2ec8-4ac0-86bd-b30499d8e9ed ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb1.
title		Ubuntu 7.10, kernel 2.6.22-14-generic (on /dev/sdb1)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=d1f8a7a6-c7c9-4ec0-a325-eb4d6e979714 ro quiet noresume rootflags=data=writeback 
initrd		/boot/initrd.img-2.6.22-14-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb1.
title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode) (on /dev/sdb1)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=d1f8a7a6-c7c9-4ec0-a325-eb4d6e979714 ro single rootflags=data=writeback 
initrd		/boot/initrd.img-2.6.22-14-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb1.
title		Ubuntu 7.10, memtest86+ (on /dev/sdb1)
root		(hd1,0)
kernel		/boot/memtest86+.bin  
savedefault
boot

```

I've got Ubuntu on one disk, and Kubuntu on the other.

Bob

---

### Post by Mark_in_Hollywood on 2007-11-11
Ahh . . . I would that things went smoothly, BUT:

I decided to take the plunge and put the Gutsy (tribe 2) LiveCD in the drive and set the BIOS to read it first. 

It wouldn't do that.

I found my Canonical Feisty LiveCD and tried it. Booted right up. I found the "Step 5" which asks here to put the OS, selected my 40 gig which sits as pri/slave. An hour later it was up and running. I then did the OS Upgrade, and another hour and I'm now running Gutsy on both disks. The Feisty even asked if I wanted my settings from the pri/slave, which came through just fine.

I've changed my mind and decided to put on the ext3 on the the pri/master. Can you tell me how to do this?

By the bye; I'm relocated /home to the 40 gig and am a happy-camper.

One more step and this thread can be marked SOLVED.

---

### Post by RTrev on 2007-11-11
> **Mark_in_Hollywood said:**
> 
I've changed my mind and decided to put on the ext3 on the the pri/master. Can you tell me how to do this?

Before we screw up your entire system, I need to be 100% certain I understand what you mean by "put the ext3 on the pri/master".  By using the phrase "the ext3" it sounds like you think this is a partition, or some other tangible "thing" which can simply be moved from one place to another.  Ext3 is a file system.  Let's make sure we're on the same page before we do anything.

What do you mean by your "ext3"?  What is it?  I'm sure this won't be too hard, but, if we're not completely in agreement about the goal, chaos is certain to result.  :)

Bob

---

### Post by Mark_in_Hollywood on 2007-11-11
Per your earlier suggestion, I am going to put the data (mostly mp3 files) on the 20gig, which sits on the cable as Primary/Master.

Sorry for the inconvenience/incommunication. I want to treat the pri/master as a place for storage, not for executable programs, or the entire Gutsy OS. I hope this helps.

You might recall "formatting" a floppy disk without the "system" on it. The disk reached max storage space that way. That is what I want with the 20 gig pri/master.

---

### Post by RTrev on 2007-11-12
> **Mark_in_Hollywood said:**
> Per your earlier suggestion, I am going to put the data (mostly mp3 files) on the 20gig, which sits on the cable as Primary/Master.

Sorry for the inconvenience/incommunication. I want to treat the pri/master as a place for storage, not for executable programs, or the entire Gutsy OS. I hope this helps.

You might recall "formatting" a floppy disk without the "system" on it. The disk reached max storage space that way. That is what I want with the 20 gig pri/master.

Which drive is all of your GRUB stuff on at the moment?  Sorry, I've kind of lost track.. but I think you booting from the disk you want to "reformat."

If you're booting from the master disk, you'd lose your boot completely if you wiped the disk.  Better have somebody who understands the GRUB stuff better than I do tell you how to move it to the other disk.  I still don't know most things about the entire boot process, and what I've learned has been trial and error.  <g>

"Formatting" in Linuxland is just a matter of using a partition editor like cfdisk and setting whatever partitions you might want, such as just one big one for the entire disk, and then running the appropriate utility to put a file system on the partition.  In this case it would be mkfs.ext3.

Bob

---

### Post by Mark_in_Hollywood on 2007-11-12
Roger, wilco

The Foxconn motherboard I have allows me to select the boot priority of the hard drives. So I have it booting to the 40 gig and will get a copy of GParted, which I've used before and re-set the 20gig's partition.

Thank you, Bob.

---

### Post by RTrev on 2007-11-12
> **Mark_in_Hollywood said:**
> Roger, wilco

The Foxconn motherboard I have allows me to select the boot priority of the hard drives. So I have it booting to the 40 gig and will get a copy of GParted, which I've used before and re-set the 20gig's partition.

Thank you, Bob.

Just a thought, but the OS doesn't take that much room.  Have you thought about using the big drive for the data, and the smaller one for the OS?

I have a 74G disk for the OS, and two 500G disks for data.. plus an external USB 500G for backups (only one of many types of backups.)  The OS disk is pretty much empty, but the data disks fill up quickly.

GParted is something I sometimes use, although I prefer cfdisk.

Bob

---

