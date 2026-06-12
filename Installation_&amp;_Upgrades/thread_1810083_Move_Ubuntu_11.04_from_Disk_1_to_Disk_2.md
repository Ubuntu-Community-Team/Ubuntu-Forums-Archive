---
title: "Move Ubuntu 11.04 from Disk 1 to Disk 2"
date: 2011-07-22
forum: Installation &amp; Upgrades
---

### Post by tomdean@speakeasy.org on 2011-07-22
Surely, this has been asked before...  I searched and found nothing.

I have a new HP Envy 17 64-bit laptop with two drives.  It seems to have a heat problem.  HP support seems to think the BIOS is getting corrupted and wants me to upgrade it.  To do an upgrade I have to put windows 7 on the first disk.  I tried virtualbox but, could not upgrade the BIOS from there.

I have Ubuntu 11.04 on the first disk, with quite a few packages.  I tried duplicating sda to sdb and reinstalling grub on sdb.  It would not boot.

I want to move my Ubuntu installation to the second disk, install wondows on the first disk, do the upgrade, and use the first disk for something...

How do I move Ubuntu 11.04 from the first disk to the second disk?

---

### Post by MAFoElffen on 2011-07-22
> **tomdean@speakeasy.org said:**
> Surely, this has been asked before...  I searched and found nothing.

I have a new HP Envy 17 64-bit laptop with two drives.  It seems to have a heat problem.  HP support seems to think the BIOS is getting corrupted and wants me to upgrade it.  To do an upgrade I have to put windows 7 on the first disk.  I tried virtualbox but, could not upgrade the BIOS from there.

I have Ubuntu 11.04 on the first disk, with quite a few packages.  [COLOR=Red]I tried duplicating sda to sdb[/COLOR] and reinstalling grub on sdb.  It would not boot.

I want to move my Ubuntu installation to the second disk, install wondows on the first disk, do the upgrade, and use the first disk for something...

How do I move Ubuntu 11.04 from the first disk to the second disk?
Please read the whole post before doing something...

> HP Envy 17 64-bit laptop-- 640 GB SATA Hard Disk Drive 7200 rpm
Looking at the specs of your laptop from HP... Like most laptops, it shows that it has one physical 2.5 inch hard drive partitioned into 2 partitions, which would look to Win7 as 2 logical drives...  Laptops usually have room for 1 physical internal hard drive. That would mean you really have something more like sda1 and sda2...

Two ways to confirm that would be first to 
```

sudo blkid

```Which will show the physically drives and their partitions. Second would be just to look for the drive in the BIOS.

But-- I volunteer for a computer recyclers where, besides recycling and rebuilding computers for sale, we also repair and upgrade computers for customers...  When we have to upgrade a computer's BIOS or it's hardware's firmware, we usually use a USB pendrive, USB attached floppy drive or USB attached hard drive...  That way we don't have do anything with a customer's installed OS.

Next, if you looked at this thread:
[http://ubuntuforums.org/showthread.php?t=1745389](http://ubuntuforums.org/showthread.php?t=1745389)

It would then beg to ask you if the over-heating problem you are experiecing is just the known kernel bug where: "in Natty that can drain the battery and overheat the computer."   If so, then updating the BIOS would not fix it... but this workaround would help:
[http://www.webupd8.org/2011/06/linux-kernel-power-issue-fix.html](http://www.webupd8.org/2011/06/linux-kernel-power-issue-fix.html)
[URL="http://www.webupd8.org/2011/06/linux-kernel-power-issue-fix.html"]
[/URL]

---

### Post by tomdean@speakeasy.org on 2011-07-22
The laptop came with RAID0 enabled so the two disks looked like a 1.2TB disk.  I disabled RAID, installed Ubuntu 11.04 on sda.  Ubuntu thinks there are two drives.  600GB (+-) a total of 1.2TB.

I duplicated sda to sdb with clonezilla-live 1.2.8-46 amd64.

blkid shows two drives.

---

### Post by MAFoElffen on 2011-07-22
> **tomdean@speakeasy.org said:**
> The laptop came with RAID0 enabled so the two disks looked like a 1.2TB disk.  I disabled RAID, installed Ubuntu 11.04 on sda.  Ubuntu thinks there are two drives.  600GB (+-) a total of 1.2TB.

I duplicated sda to sdb with clonezilla-live 1.2.8-46 amd64.

blkid shows two drives.
And they both show in the BIOS?  And you can toggle which drive is the primary boot drive in the Bios?  And the boot flag is set on the partition in the second drive?

Just continuing with what you are trying to do...  If so, then boot from a LiveCD, mount and change root to the second drive and reinstall grub to it-- which will write the boot sector/mbr.  (You can do the same if you can still boot from your original install on sda.)  Need instructions?

Then "it should" boot Ubuntu from that second drive, independently from the first.  Installing Win7 on the first "then" shouldn't affect the second drive.

EDIT-  I forgot to mention the why of reinstalling Grub2 to sdb...  Clonezilla cloned your disks as a mirror.  So the pointers in grub on the second disk are presently looking at the UUID of the first disk... which is going to be overwritten by Win7.  There's various ways to change and correct this.  I just figure the way I suggested would be easiest and fastest.

---

### Post by tomdean@speakeasy.org on 2011-07-23
Ok, I finally managed it.  The laptop really has two disk drives!  toshiba MK6461GS.  One id 0x000280a0 the other id 0x0003e46c.

  installed Ubuntu 11.04 on sdb
  installed windows 7 on disk 0, leaving half for a future FreeBSD install

  booted windows 7
  downloaded and installed easyBCD.  There is a free version.
  In easyBCD, add a new entry,  linux and select grub 2
      I named it 'Ubuntu 11.04'  But, that does not matter.

All done.

Thanks for all the help.

tomdean

---

