---
title: "More partitioning woes."
date: 2006-08-04
forum: Installation &amp; Upgrades
---

### Post by ko16736 on 2006-08-04
I need some advice on what to do next. Please note that I am currently using the Live Cd for Dapper Drake and I am a complete "n00b".

I have a 60 gb harddrive in my laptop, My Windows XP partition (that I want to dual boot with) was taking up 50 gbs. So I resized that partition using GParted on the Live CD, and it is now taking up 35 gbs. I have 5 paritions listed in GParted, this is what GParted looks like:

Partition    Filesystem     Size     Used        Unused       Flags
/dev/sda1     fat16       39.19MB    7.48MB      31.71MB
/dev/sda2      ntfs       34.18GB    24.15GB     10.03GB      boot
unallocated   unallocated 15.62GB    ---           ---
/dev/sda3      fat32      4.64GB     3.59GB      324.52MB
unallocated   unallocated 760MB     ---           ---

I do not really know what the fat16 and fat32 part is, unless its part of the BIOS or they're system recovery tools or something, I am not really all that great with computers.
I want Ubuntu to go in that 15.62GB partition, but I don't know what to do when I get to the "Select a disk" part of the Installation. Your help would be much appreciated.

---

### Post by ko16736 on 2006-08-04
Oh come on now, someone just has to have all the answers to my not knowingness.

---

### Post by Jagot on 2006-08-05
When using the alternate install cd it offers you the option of 'guided partitioning' at the partitioning stage.  Selecting that you can then choose to use the largest free space and it will install and set up a swap partition automatically for you.

In the desktop (live) cd use manual partitioning.  You just need to set up a swap partition - depending on your RAM its usually somewhere between 512MB and 1GB.  The use the res to allocate a partition is /.

You may want to check out these guides:

[http://psychocats.net/ubuntu/installing.html](http://psychocats.net/ubuntu/installing.html)
[http://users.bigpond.net.au/hermanzone/p3.htm](http://users.bigpond.net.au/hermanzone/p3.htm)

---

