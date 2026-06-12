---
title: "SERIOUS Installation error 8.04, grub fails to load, system unbootable"
date: 2008-04-25
forum: Installation &amp; Upgrades
---

### Post by hahnson on 2008-04-25
I have encountered a error that makes grub fail after installation, rendering the system unbootable. This seems to be caused when mixing ide and sata and/or different devices. When i installed 8.04 on my server which holds 10 ide drives of which three are connected to the mainboard and the remaining connected to one of two promise ultra 133tx2 pci ide controller cards.

When making partitions my main drive, connected as master on primary on mainboard, gets designated as /dev/sdi, all drives are dessignated as SCSI (eg SCSI#2 0.0.0). install completes ok but when rebotting, grub fails, stating various errors.

Since my machine worked allright with earlier version, this seems to be a problem caused by the installer, and there is a bug report filed [https://bugs.launchpad.net/ubuntu/+source/grub-installer/+bug/14135](https://bugs.launchpad.net/ubuntu/+source/grub-installer/+bug/14135)

i have tried to reinstall grub and installed with the alternate cd without luck, if any one got suggestions what to do about it, to get my computer up and running again.

i have tried this on another computer with both sata and ide drives. when installing with only sata or ide i dont encounter any problems, but when i mixed it failed with the same error.

---

### Post by Pumalite on 2008-04-25
This might help:
[http://ubuntuforums.org/showthread.php?t=46003](http://ubuntuforums.org/showthread.php?t=46003)

[http://ubuntuforums.org/showthread.php?t=567907](http://ubuntuforums.org/showthread.php?t=567907)

[http://ubuntuforums.org/showthread.php?t=593615&page=2](http://ubuntuforums.org/showthread.php?t=593615&page=2)

My solution to this problem has been, in the past, to install all OS to the first drive and use the rest as storage or separate /home.

---

### Post by hahnson on 2008-04-25
> **Pumalite said:**
> This might help:
[http://ubuntuforums.org/showthread.php?t=46003](http://ubuntuforums.org/showthread.php?t=46003)

[http://ubuntuforums.org/showthread.php?t=567907](http://ubuntuforums.org/showthread.php?t=567907)

[http://ubuntuforums.org/showthread.php?t=593615&page=2](http://ubuntuforums.org/showthread.php?t=593615&page=2)

My solution to this problem has been, in the past, to install all OS to the first drive and use the rest as storage or separate /home.
 

ok but that sulotion is not applyable in my situation, i have data on al those drives and i don't want to run my os on the pci conntroller, very bad for performance.

but i think i have solved the trouble by removing the controillers and install, only thing left is to se if it still works when i plug them back, but i am VERY annoyed of this error whith a LTS release one doesent expect such serious errors to be present, strange it is present on the finnal since it has been confirmed on the rc before

thanks anyho:)

---

### Post by Pumalite on 2008-04-25
Mix of IDE and SATA seems to be a bad idea with any Linux.

---

### Post by hahnson on 2008-04-25
> **Pumalite said:**
> Mix of IDE and SATA seems to be a bad idea with any Linux.

i dont hav any scsi, all my drives are ide, but i use a non scsi pci ide conntroler, it has worked perfectly before. i managed to install ubuntu 8.04 by removing the controllers and put them back after installaton and now it boots, so there is an error in the installer that caused the problem. this has newer ockured before.

---

### Post by OldFart2 on 2008-09-06
I have had the exact same issues with nearly every version of Linux I have tried --- the installer NOT being able to correctly identify the hard drive I CHOOSE to install the bootloader to. The cause always seems to be a combination of SATA and PATA drives connected to the motherboard and a PCI controller (RAID or otherwise).

The ONLY solution I've found that actually works is to disconnect ALL the other hard drives and leave ONLY the drive connected I want to install Linux and GRUB to. That really pisses me off because I HATE taking the lid off my computer and having to disconnect cables (disabling a controller in the BIOS obviously doesn't work).

You wouldn't think this was rocket science, but apparently it is. I've never seen such a BIG problem with any other operating system, in that Linux installers just flat fail to correctly install GRUB to the desired drive. I don't really think it has anything to do with GRUB either as I've experienced the same problem with LILO. 

Just yesterday I tried to install Ubuntu 8.10 Alpha 5 on a 20GB external USB drive. There are two other drives installed --- a SATA 80GB drive and a PATA 60GB drive. Windows XP is on the 60GB drive and Ubuntu 8.04 WAS on the PATA drive. After installing 8.10, I couldn't boot to the 20GB drive, and YES --- I told it to install everything there.

To make matters worse, when I tried to boot my 8.04 drive, the installer for 8.10 had over-written its boot loader and instead of being able to boot EITHER version of Ubuntu, I could only boot the 8.10 version. I subsequently reformatted the 20GB drive and now I can't boot the 8.04 drive at all. It just never seems to end. 

THIS is the exact sort of thing that turns people off to Linux. I can just imagine the response of someone who DOESN'T have knowledge of Linux or UNIX and has mixed drives installed (a combination of SATA and PATA), which I really don't think is all that uncommon. If it were my first attempt, I'd put the Linux disc in the microwave oven or use it as a coaster and never look at Linux again.

Anyway, I didn't mean for this to turn into a rant, but it's WORTH ranting about. The pathetic state of Linux installers IS such that they can't even figure out when I TELL it to install a Linux kit AND the bootloader to a particular hard drive, that IS the drive I REALLY want it installed on. If you have mixed SATA and PATA drives, however, all bets are off and there's apparently no telling WHAT you'll end with.

Or, maybe I'm just getting grumpy in my old age.

By the way, if you haven't heard of it, there's a very handy tool available for fixing boot loader / grub issues. It's called "Super Grub Disk" and is available (FREE) for download in a variety of form (ISO, floppy format, memory stick, etc.). It is extremely easy to use and there is a plethora of help available from the site (tutorials). HIGHLY recommended and is what I used to "fix" the problem described above (the one with Ubuntu 8.10 Alpha hosing up my 8.04 boot loader). Here's the link - 

[http://www.supergrubdisk.org/wiki/Main_Page](http://www.supergrubdisk.org/wiki/Main_Page)

OldFart

---

### Post by Pumalite on 2008-09-06
Also search in this Forum for:
Dualboot Two Hard Drives

---

