---
title: "Ext3 File System Creation in Partion #1 of SCSI1(0,0,0) (sda) Failed"
date: 2008-05-22
forum: Installation &amp; Upgrades
---

### Post by peterjanda on 2008-05-22
I connected a 500 GB Maxtor ATA HDD to the IDE1 primary slot on my motherboard, and this is the only hard drive in my desktop.  I ran the 8.04 Alternate boot process all the way through disk partitioning, at which point I received the error message in the title of this post.

At his point, my best guess about the cause of the error is that my computer for some reason believes the hard drive is an SCSI device rather than an IDE device.

Does anyone have a thought about why this is happening?

---

### Post by Patb on 2008-05-22
Peter, in recent releases, Ubuntu uses scsi notation for ide drives and partitions.  It is normal.  I saw a detailed debate about the whys and wherefors but fell asleep before I could bookmark the URL ;). 

For a start, I would try booting from live CD and check the partition information you have there (if any).  Open a terminal and type:
```
sudo fdisk -l
```
> Does anyone have a thought about why this is happening?
Not a clue yet, sorry.  

Cheers, Pat

---

### Post by peterjanda on 2008-05-22
Thanks.  I'll see about the existing partitions tonight, when I get home, but I am confident they will be unenlightening.  For simplicity, just to get the OS up and running, I opted for a guided partition process that generated a 1.5 GB swap partion and a 498.5 GB root partition.

My plan B is to attempt an XP install to assess whether Windows has similar issues.  If yes, my thought it must be an HD, motherboard, BIOS and / or user problem.  If no, it must be a Ubuntu problem.

Pete

---

### Post by Patb on 2008-05-22
> **peterjanda said:**
> My plan B is to attempt an XP install to assess whether Windows has similar issues.
Sounds a good idea, Pete.  Also you may wish to partition the disk using the gparted live CD: [http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php) 

Search the forum for partition advice too.  You might consider a separate /home partition: 
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

Cheers, Pat.

---

### Post by yotam on 2008-05-23
See [URL="https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/99908"]https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/99908  
titled:
**The ext3 file system creation in partition #1 of SCSI1 (0,0,0) (sda) failed.**
[/URL]

---

### Post by Patb on 2008-05-24
Pete, from the looks of discussion on the bug report that Yotam pointed out, you might try partitioning your disk using the gparted live CD and then install Ubuntu using manual partitioning using the partitions you have already set up.  

Cheers, Pat.

---

### Post by peterjanda on 2008-05-24
Thanks all for the additional thoughts, though I think the root of the problem lies elsewhere.  I attempted to install XP and received a similar error.  After attempting to format the HD, XP informed me that it could not do so.  The great news is that this particular instance of this error is unlikely to be Ubuntu related.  The bad news is that the issue is most likely related to my antiquated hardware.

After spending the last two days researching (on and off) the southbridge chips integrated on my motherboard, I have come to the guesstimate that the chips lack native functionality to correctly interface with a new 500 GB drive.  I have:

- Highpoint HPT372 for RAID functionality on the IDE3 and IDE4 slots

- VIA VT8235 for everything else, including interfacing with IDE1 and IDE2 slots

I checked these two chip OEMs' respective Web sites for up-to-date drivers / support and discovered that Highpoint doesn't appear to support its 372 chips anymore and VIA hasn't heard of Ubuntu.

I'm calling it a day on this, taking out the 500 GB drive and putting back the two old 40 GB drives that worked just fine with the motherboard.  Sorry to have consumed time on this board with what turned out to be (most likely) hardware problems on my end.

Pete

---

### Post by Patb on 2008-05-25
> **peterjanda said:**
> Thanks all for the additional thoughts... Sorry to have consumed time on this board
Not at all, Pete.  Thanks for posting your own conclusions.  Cheers, Pat.

---

