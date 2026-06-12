---
title: "New machine has 4 primary partitions; unallocated space &quot;unusable&quot;"
date: 2010-02-10
forum: Installation &amp; Upgrades
---

### Post by starsprout on 2010-02-10
Hi-

My motherboard on my old HP laptop died, so I bought a new machine that's running Windows 7.

The machine is a Compaq (HP) and has a 250 Gig hard disk. I used Windows Disk Manager to shrink the space Windows is in so I can install Ubuntu in that space.

When I start the partitioner it says the free space is unusable. I ran Gparted and sure enough, there are already 4 primary partitions on my drive:

/dev/sda1 = ntfs - SYSTEM
/dev/sda2 = ntfs
unallocated
/dev/sda3 = ntfs - RECOVERY
/dev/sd4 = fat32 - HP_TOOLS

The "SYSTEM" partition shows a size of 199 MiB with 66 MiB used and 132 MiB unused (which is confusing to me because I thought I shrunk that partition).

Anyway, I seem to already have 4 primary partitions on this machine.

How do I proceed with a Dual-Boot Ubuntu installation from here?

All help is most appreciated - thanks!

---

### Post by darkod on 2010-02-10
I'm just having the same discussion with someone else about their HP laptop. :)
Read here and do what ever you think is best for you:
[http://ubuntuforums.org/showthread.php?t=1403414](http://ubuntuforums.org/showthread.php?t=1403414)

Post any questions you have.

---

### Post by Mark Phelps on 2010-02-10
BEFORE you do anything else, use the builtin Win7 function to create and build a Win7 Repair CD.  You might need this later if you run into boot problems during dual-boot setup.

I'd ordinarily recommend using the Win7 Disk Management utility to move the Recovery partition adjacent to the Win7 partition, but I don't know if that will hose up recovery on your machine.

If you do that move, I would then back off the complete contents of the HP Tools partition to an external drive or DVD (presuming it's small enough to fit on a DVD.

That will leave you an unallocated space at the end of your drive in which to install Ubuntu.

---

### Post by starsprout on 2010-02-10
Ok - I've done the research (even spoke with HP support) and have decided it's ok to delete my HP_RECOVERY partition.

I went through the HP (Compaq) Recovery Manager Software in Windows 7 and created a 3-DVD recovery disk package so that's good. I will use the same program "Recovery Manager" to delete this partition, as is recommended by HP and some other forums.

Before I realized what was up, when I started this process, I used Windows Disk Manager to "shrink" the Windows volume. Of course the space I created was "unusable" but once I delete the HP_Recovery partition I'll be able to right? Or do I need to "undo" the shrink or start over in some way?

Am I good to go forward deleting the HP_Recovery partition  with the Windows disk manager shrink already performed?

Thanks!

---

### Post by starsprout on 2010-02-11
Here's where I am.

I performed the following on my new Presario laptop:

-Used Windows 7 Disk (Computer) Managment to shrink the system space
-Used HP Recovery Manager to create 3/3 DVD Backups of the system
-Used HP Recovery Manager to deleted HP_RECOVERY partition
-Used Windows 7 Disk (Computer) Management to delete HP_TOOLS partition

Now, when I look at my HD in either Windows Disk management or in Gparted, I have a 108 MB "unallocated" thing on my HD. It's not a partition, but just space. What is that? Does it matter? Can I delete it? Do I need to delete it? (I can't figure out how) Will I need it later?


(aside: In over 6 years running HP (and WinXP) I've never needed either HP_TOOLS or HP_RECOVERY or even the recovery disks.)

---

### Post by darkod on 2010-02-11
Unallocated space on your hdd is just that, space which is not allocated in any of the partitions. You can expand a neighboring parition to include those 108MB but for that small amount of space it's not worth the risk. There is always some small risk when resizing partitions.
And to answer your earlier question, it's fine that you first shrank windows but were not able to install ubuntu because you already had 4 partitions. Now that you deleted two of them, you can use the same space that you planned to install onto, or make other plans for the layout because the HP RECOVERY partition probably freed a significant amount of space for you (depending how big it was).

---

### Post by starsprout on 2010-02-11
It is done. I deleted both HP Partitions.

I'm running Ubuntu 9.10 64-bit alongside Windows 7 - woo hoo!

Now working on getting optimal sound (pretty much done with that, just trying different alsa-base.conf options) and graphics.

Thanks for the help here folks!

---

