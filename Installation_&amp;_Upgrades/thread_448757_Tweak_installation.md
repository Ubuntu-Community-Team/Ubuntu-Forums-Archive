---
title: "Tweak installation"
date: 2007-05-19
forum: Installation &amp; Upgrades
---

### Post by jhenrik on 2007-05-19
:KSHistory:  Installing Ubuntu into an existing WinXP Home system.  The system uses an Abit KT-7A Raid motherboard.  Raid was not activated, allowing two additional IDE channels.  Thus a total of four IDE channels for a possible eight devices.  Under XP, IDE channel 1 Master was a DVD-RW, IDE channel 2 Master a CD-RW.  The Slaves 1 and 2 were unused.  IDE channels 3 & 4 are controlled by the built in HPT 370 raid controller bios.  Hard drives (total of four) were attached to the Master and Slave of each channel.  IDE 3 Master was the WinXP boot disk.  This configuration ran well for a number of years.

To install Ubuntu, a hard disk (IDE 3 Slave) was cleaned off and made the Master.  Ubuntu was installed on it without problems, but the system would not boot.  Several attempts were made and several bios combinations tried, but could not get beyond a computer reboot loop.  The Grub screen never appeared.  With Ubuntu as the IDE 3 Master there were problems.  

Changing disks to IDE 1 (Ubuntu Master and WinXP Slave) cleared the problem and allows full dual boot capabilities.  Configuration is now:  IDE 1 Master Ubuntu disk, Slave WinXP; IDE 2 Master DVD-RW, Slave empty;  IDE 3 Master and Slave, both Fat 32 disks; IDE 4 Master CD-RW, Slave empty.  Ubuntu installation runs fine.  All updates and upgrade to 7.04 made.  

Casualty:  WinXP recognizes all devices but the IDE 4 master CD-RW.  Highpoint site indicates their Raid controller bios recognizes only formatted hard drives.  Would like to copy from one CD to the other without caching, but can live without it.

Current Issues:  Ubuntu recognizes all disks in device manager, but the browser does not show the IDE 3 master disk.  How do I make this disk available?

The full name of the IDE 3 Slave was changed from the XP name, but contents are available to Ubuntu.  Would like to keep consistent names. Is this normal?

Is there a way to make the system bootable with Ubuntu installed on the IDE 3 Master disk?

---

