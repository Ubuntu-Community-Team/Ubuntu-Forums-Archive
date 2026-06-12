---
title: "Dual disk/dual boot install advice needed"
date: 2005-02-15
forum: Installation &amp; Upgrades
---

### Post by demeiss on 2005-02-15
I have not yet downloaded Ubuntu, but I intend to install it on a new second hard drive, leaving the current WinXP installation on the existing C:\ drive.  I have been looking at various Ubuntu and Linux website help pages, but I'm not sure I see how to add the dual boot partition to the original unpartitioned C:\ drive (40-Gig IDE), and then install the rest of the OS and application software onto the new drive.

Is this a daunting task to perform without damaging the existing XP installation?  Do I need additional software?  

Any advice greatly appreciated,
Dennis

---

### Post by tkiesel on 2005-02-15
Hi Dennis,

Last week, I installed Ubuntu to my second hard drive. I cleared all of my data off that drive in preparation for the install, then popped in the CD that I'd finally managed to burn correctly and booted up into the Ubuntu installer.

To make a long story short, things preceeded from there without trouble. The install program automatically put the GRUB bootloader on my primary (Windows XP) hard drive. Now, when I boot up, I get a menu right after the BIOS loads that allows me to select if I want to run Windows XP or Ubuntu.

It wasn't daunting, and required no extra software.

It worked like a charm for me, and I'm now dual-booting at home, and finding myself choosing XP less and less as I get more comfortable in Ubuntu. (Still can't print from Ubuntu to a shared printer on my brother-in-laws XP box though. ;) I'll figure that one out eventually)

One thing I did do was take the time to read up and understand how the partitioning tool in the Ubuntu installer works. The defaults will work just fine, so don't get worried about breaking the install of Ubuntu, but learning how it worked allowed me to create the partitions that Ubuntu needed and reserve the lion's share of my space on that hard drive for a FAT32 partition where I can store my music and movies, so I can have those same files in both Windows and Ubuntu. :)

Good Luck,
T

---

