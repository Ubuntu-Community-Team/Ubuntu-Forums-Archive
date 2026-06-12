---
title: "UNR Installation problem"
date: 2010-01-04
forum: Installation &amp; Upgrades
---

### Post by buggo on 2010-01-04
Hi,

I have a new Samsung N140 notebook with standard specs (Atom 280, 1GB, 250GB etc). I successfully downloaded and installed UNR to a USB stick (2GB). This boots perfectly and everything functions well (slight config to get wireless working). 

I like what I see and now want to install in a partition on the HDD. 

Whilst booting perfectly from the USB stick, after a HDD install (started from Ubuntu USB system or at boot time) the boot process progresses to a point then presents a dim white screen that changes to a blank screen and back every few seconds, flashing or blinking. There is no blinking cursor as has been reported in other threads. 

When I flick the power switch it shuts down normally so it doesn't appear to be hung.

Sounds like a monitor driver problem, but why does it boot fine from the USB? Could it be partitioning (sounds unlikely)? Here is partitioning info.Drive comes with 2 existing partitions 

15gb Recovery partition NTFS (/dev/sda1)
100mb boot? partition NTFS (/dev/sda2)

It now has a further primary partition for Windows 7 

30gb Win7 partition NTFS (/dev/sda3)

Obviously I can only now create an extended partition, with logical drives. 

187gb extended partition (/dev/sda4)

consisting of-
8gb Ubuntu partition EXT3 (/dev/sda6) - I have also tried unsuccessfully the EXT4 FS
2gb Linux Swap partition (/dev/sda7)
177 storage partition NTFS (/dev/sda6)

The last thing the screen displays is a message that states something like "loading fonts and keymap"?

I have been searching for a solution for 2 days now and it is time to either ask the experts or give up.

Regards,

Mike

---

### Post by buggo on 2010-01-05
I should have also stated that I want to dual boot with the already installed Win7 and for the time being keep the recovery partitions. Hence having to install in an extended partition.

Mike

---

