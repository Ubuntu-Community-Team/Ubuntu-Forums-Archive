---
title: "Installation Partion Manager Doesn't See Harddrives"
date: 2010-07-25
forum: Installation &amp; Upgrades
---

### Post by phillipi on 2010-07-25
Trying to install Ubuntu 10.04 onto my computer.  Trouble is when I get to the part of installation to select partitions its blank.  I have tried the 32 bit and 64 bit versions.  I also tried to install Fedora 13, LinuxMint 9, and PCLinuxOS and met with the same problem.  

I checked the cmos and it is seeing my harddrive.  I installed Windows 7 on this computer with no problem.  

I opened up GParted on the Ubuntu LiveCD and GParted saw my harddrive and my partitions.  I removed all of my partitions and tried to install again.  Again the installation partition manager sees nothing.

As another experiment I stuck a 2gb thumbstick into my USB and booted up the Ubuntu LiveCD.  When I got to the partion part of the install it saw my thumbstick but not my harddrive.

So GParted sees my drive, the cmos see my drive, and Windows 7 sees my drive.  Why wont the Ubuntu Installation see it?  I tried re-downloading and re-burning the cd several times.

---

### Post by quixote on 2010-07-27
Maybe try checking the flags when you're in gparted.  Is there a chance the non-windows partitions somehow became hidden or archived or something?  Or maybe Windows flagged it as being visible only to Windows??  It's interesting that all the linuxen have the same problem, and what they all share is a similar way of handling drive permissions.

---

### Post by dabl on 2010-07-27
The Ubiquity installer doesn't always see some kinds of drives.  If it is a SATA drive, you can go into BIOS and change the mode to "Legacy IDE" -- sometimes that works.  Other times you might need to use the Alternate Install CD, which does not use Ubiquity.

---

