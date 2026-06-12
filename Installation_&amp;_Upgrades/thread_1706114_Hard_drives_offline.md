---
title: "Hard drives offline"
date: 2011-03-13
forum: Installation &amp; Upgrades
---

### Post by Lar56 on 2011-03-13
I installed Ubuntu 10.04 in a Raid 0. The install went fine. When I shut down my machine then boot it back up it shows no raid volumes defined and my hard drives as offline. Then the Disk boot error message. I am new to Unbuntu and I am sure the solution is simple I just need to know what to do. Thanks!

---

### Post by runeh76 on 2011-03-13
Hi

How did u partitioned ur disks?
Have u seen this:
[https://help.ubuntu.com/community/Installation/SoftwareRAID]("https://help.ubuntu.com/community/Installation/SoftwareRAID")

---

### Post by Lar56 on 2011-03-14
I have 2 500GB Seagate HDD's. My primary partition = 990Gb / ext4, Logical = 7.4GB Swap and 2.4GB = Freespace

---

### Post by Hedgehog1 on 2011-03-14
lar56,

You cannot boot from a software RAID 0. It must be RAID 1. I am helping another person with this same thing right now:

[http://ubuntuforums.org/showthread.php?t=1706499]("http://ubuntuforums.org/showthread.php?t=1706499")

Take a look.

***The Hedge***

:KS

---

### Post by Lar56 on 2011-03-14
Thanks Hedge, looks like I need to do more study. I'll let you know what I come up with.

---

### Post by Lar56 on 2011-03-14
Ok Hedge, I looked at your link, and what I am understanding is in order to run Unbuntu in a Raid0 I would need a 3rd HDD in order to set up a Raid1 boot device. Am I right?

---

### Post by Hedgehog1 on 2011-03-15
Here is the thing with SOFTWARE RAID, you need a real 'unsliced' disk to boot.

You can boot from RAID1 because both drives are complete, and you really boot off of one of them, load the software for RAID off that same drive, and *****then** they work are a mirrored team.***

You cannot boot from a SOFTWARE RAID0 because no single drive has a complete set of data.  To use SOFTWARE RAID0 you do need to boot from a 3rd real (data not sliced up) drive, load the software for the RAID, and then you are running.

As a side note: RAID0 is just asking for pain.  If one drive fails, all data is lost.  It is fine for learning, but please use RAID1 for reliability long term.

***The 'Practice Safe RAID' Hedge***

:KS

RAID 0 - Data is sliced between drives:
[IMG]http://upload.wikimedia.org/wikipedia/commons/thumb/9/9b/RAID_0.svg/150px-RAID_0.svg.png[/IMG]

RAID 1 - Two complete images working as a team:
[IMG]http://upload.wikimedia.org/wikipedia/commons/thumb/b/b7/RAID_1.svg/150px-RAID_1.svg.png[/IMG]

---

### Post by Lar56 on 2011-03-15
Thanks Hedge I was beginning to understand what you said from doing my own research. Some "how to" articles don't give complete info on how to do things. I am assuming it would be very wise to purchase an external hard drive and use it for back up in the event I want to run a Raid0.

---

### Post by runeh76 on 2011-03-15
sry, i dont understand why u are using raid?
If u have two HD.s just take img backup, like once per week.
U can use Clonezilla. Boot it CD or USB-stick.
[http://clonezilla.org/](http://clonezilla.org/)

---

### Post by Hedgehog1 on 2011-03-15
> **Lar56 said:**
> Thanks Hedge I was beginning to understand what you said from doing my own research. Some "how to" articles don't give complete info on how to do things. I am assuming it would be very wise to purchase an external hard drive and use it for back up in the event I want to run a Raid0.
 
If your reason for running RAID 0 is 'reading' speed, RAID 1 is just as fast for reading. RAID 1 is a little slower for writing, but that is because you really get fault tolerenace with RAID1 because there is a copy of everything.
 
A true hardware raid controller with a heathly amount of Memory and async lookups will give you the very best possible prformance.  If the unit is 'hot swappable', even better.
 
**runeh76 **askes about making backups weekly, rather than run RAID.  This is what I tend to do.  There are some things I don't bother backing up (downloaded Simpson episodes I missed, I can downthem them again of the disk dies), but family photos and purchased mp3s get burned to a data DVD or BluRay promptly, as well as copied to an external disk.
 
***The Hedge***
**** 
:KS
 
p.s. If you want, we can talk about the speed advantages of async lookups for busy databases on RAIDs.  Fun stuf (well, to me, anyway).

---

### Post by Lar56 on 2011-03-15
Hi guys, I wanted to use Raid0 for better performance. Computers are just a hobby for me. I don't use one for work, and I don't have data that I need to back up on a regular basis. I thought Ubuntu looked like a cool OS so I thought I would give it a whirl. Thanks Hedge for the invitation on async lookups, but I think you would be over my head in about 5 seconds:)

---

### Post by Hedgehog1 on 2011-03-16
We learn best by doing.

If RAID0 is what you want to try, then so be it!

You will need a boot drive then.  It will be /dev/sda.

Then build the RAID 0 out of /dev/sdb and /dev/sdc (your two identical drives).

The system will boot on sda, load the software to support the RAID 0 on sdb & sdc, and start running raid.  You can mount the 'raid drive' manually, or find it's UUID and add it to your fstab file.

***The Hedge***

:KS

---

