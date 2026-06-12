---
title: "Stuck on 'detecting file systems'"
date: 2005-02-05
forum: Installation &amp; Upgrades
---

### Post by BZRK on 2005-02-05
Hello,

I wanted to finally give Linux a try, and found Ubuntu to be most interesting.
But I'm having a problem installing it.

All goes well untill it gets to the point where it is 'detecting file systems'.
There it stalls at 76% and nothing happens anymore.

I have 3 disks (2 PATA, 1 SATA) and 4 partitions, all have NTFS on them.

What am I doing wrong or what am I missing here?
Any help would be appreciated, but please keep in mind I'm totally new to Linux.

Thx in advance

---

### Post by newmonkey on 2006-10-11
I'm actually having a very similar problem, the only difference being that it hangs at 15% instead of 75%.

Now here's the weird thing--it's not freezing. I can move the mouse, click elsewhere. I even see the CD-ROM light glow every few moments. Any thoughts?

I'm installing on a Compaq Presario M2105US laptop. 256MB Ram, 40 gig hard drive. AMD Sempron 1.4 GHz, I believe.

I'd really appreciate any feedback or thoughts about how to get around this. I have experience with Red Hat/Fedora and Gentoo but I am new to Ubuntu.

Many thanks in advance,
Robby

---

### Post by newmonkey on 2006-10-11
Well while I wait for a reply, here's what I'm going to try:
Booting in "safe graphics" mode at 640x400x16 vga.

My thinking is that because the video memory is shared, this will allow the installer to use more physical memory, thus allowing it to compensate for whatever is causing the hangup. I'm still not sure whether it was hanging or just really slow, but it haden't progressed in about 80 minutes so I thought this was worth a shot.

I'll post back and let ya'll know if I have any luck :)

---

### Post by newmonkey on 2006-10-11
It worked!:)

---

### Post by mpeppers on 2006-10-13
I just ran into this problem today, same as newmonkey's problem.  Thanks for the tip newmonkey, but it didn't work for me.  I'm still stuck at 15% "Detecting file systems..."

Anyone have any ideas?  I'm trying to install on top of a hardware SCSI RAID 5 array of 8 250-GB hard drives (so 1.7 TB usable).  I choose to format the whole 1.7 TB, and the installer first gives an "Error: no root directory" or something like that, then continues to 15%, and hangs.

---

### Post by mpeppers on 2006-10-15
I can install with no problems if I don't enable RAID.  If I just install with 8 disks, no problems.  But if I combine disks using the lower-level RAID utility, then try to install, the partitioner reports negative space available (-666307 MB available with 1 disk normal and 7 disks in a RAID).

I'll keep checking this thread for suggestions, and I'll post here when I resolve the problem.

---

### Post by mpeppers on 2006-10-15
Whew, I resolved the problem! :D   For any poor souls who run into this in the future, I'll describe the resolution.

I basically went oldschool and used the command line utilities for partitioning and formatting the disk, instead of using Ubuntu's pretty GUI partitioner.  It's been a long time since I last used fdisk, but here are the steps:

I opened a terminal and ran

$ sudo fdisk /dev/sda

fdisk is used to create partitions.  Press 'n' to create new partitions, then simply follow the prompts.  I greated a 1 GB on /dev/sda1, another 1 GB on /dev/sda2, and gave the rest of the space (~1.6 TB in my case) to /dev/sda3.

Next I had to use mkfs to make the file systems.  I chose ext3:

$ sudo mkfs -t ext3 /dev/sda1
$ sudo mkfs -t ext3 /dev/sda3

I then used mkswap to make the second partition a swap partition:

$ sudo mkswap /dev/sda2

Finally I ran the installer, and chose "manually partition" when I came to the appropriate window.  Ubuntu's partitioner saw my partitions, and allowed me to assign /boot to /dev/sda1, swap to /dev/sda2, and / to /dev/sda3.

I hope this helps, should anyone need it!

-Mark

---

### Post by Kleenux on 2007-07-31
I got the same problem (15% stuck - detecting file systems).
After a reboot and analysis of the situation it seems there is a bug in the installer: it makes a kind of mix between the previous partition table and the new one - probably trying to detect older file systems to save any data (?).

Suggestion: maybe a complete deletion of the partition table first (using either Ubuntu commands or even Windows (reboot after the partition table is written)), then installing Ubuntu from the unpartitioned disk may work.


What I did: use the Alternate version of the installer (same download page as desktop) - installation is text-based but Ubuntu will still be windowed :)

---

### Post by waratah on 2007-08-06
Deleting partitions did not work.

Rebooting in graphics safe mode did not do anything.

adding acpi=off did nothing.

---

### Post by fredj on 2007-08-06
BZRK originally posted this thread asking for help with a mixed SATA PATA system. Then 
SEAMONKEY, MPEPPERS and other people jumped in and hijacked the thread to post on
completely different problems. Well done guys!! 

This reply is for the person who owns the thread i.e. BZRK and not for the other freeloaders.
BZRK goto into the bios on your motherboard and look at the Onchip Sata item and see
what the Sata disk mode is set to. This will usually be IDE, RAID or AHCI. Also since these
disks already are completely partitioned where are you going to install Ubuntu to.
Try the Alternate CD rather than the Live CD.

---

### Post by Qharos on 2008-02-01
> **mpeppers said:**
> Whew, I resolved the problem! :D   For any poor souls who run into this in the future, I'll describe the resolution.

I basically went oldschool and used the command line utilities for partitioning and formatting the disk, instead of using Ubuntu's pretty GUI partitioner.  It's been a long time since I last used fdisk, but here are the steps:

I opened a terminal and ran

$ sudo fdisk /dev/sda

fdisk is used to create partitions.  Press 'n' to create new partitions, then simply follow the prompts.  I greated a 1 GB on /dev/sda1, another 1 GB on /dev/sda2, and gave the rest of the space (~1.6 TB in my case) to /dev/sda3.

Next I had to use mkfs to make the file systems.  I chose ext3:

$ sudo mkfs -t ext3 /dev/sda1
$ sudo mkfs -t ext3 /dev/sda3

I then used mkswap to make the second partition a swap partition:

$ sudo mkswap /dev/sda2

Finally I ran the installer, and chose "manually partition" when I came to the appropriate window.  Ubuntu's partitioner saw my partitions, and allowed me to assign /boot to /dev/sda1, swap to /dev/sda2, and / to /dev/sda3.

I hope this helps, should anyone need it!

-Mark

I realize this thread got off-topic... but mine was stalling for a while on the 15%. The above commands resolved it; admittedly, I did have to log out/back in, since the installer wouldn't boot after doing them for some reason. But, works flawlessly now, thank you!

---

