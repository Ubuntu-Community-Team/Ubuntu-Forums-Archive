---
title: "&quot;Something else&quot; installation; how do I pick where to install?"
date: 2013-12-19
forum: Installation &amp; Upgrades
---

### Post by leon.buikstra on 2013-12-19
Some background (if you're in a hurry, my three questions are at the bottom)
I have an old netbook with Windows 7 and Ubuntu 11.04 on it. Since I can't seem to upgrade it easily (I don't even want to), I want to completely throw away the 11.04 install (I've already backed up my home folder to my desktop PC and the Win7 partition, and I don't care about any program settings) and install 13.10 in its place, keeping all the other partitions and what they're used for as they are. The 13.10 installer doesn't recognize Ubuntu 11.04 and just concludes I have "multiple operating systems", then gives me the option to install 13.10 "alongside the existing OSs", completely erase the entire HD or "Something else". Since I want to get rid of the 11.04 install and use that space while keeping W7, I guess I need "Something else". Sadly, the interface popping up behind that interface is rather confusing, and although I can guess what I have to do, I just want to be sure lest I lose data or have to do the install again. Some web searching didn't clear up much, since a lot of info seems either outdated, seems to assume you have more options in the first screen or assume you already know what you're doing.
The following "Devices" are there:
/dev/sda:
/dev/sda1: a ~200MB NTFS partition, the W7 loader
/dev/sda2: 40GB NTFS, has W7 on it. I don't want to modify this, but I do want to be able to access it from Ubuntu. How?
/dev/sda5: 2GB swap. I selected this and "Change"'d it to be used as a swap partition.
/dev/sda6: 100GB ext4. Selected this and "Change"'d it to "Use as: Ext 4 journaling system", ticked Format (I hope that's a quick format?) and set mount point to /. Is that enough for the installer to understand it should install all Ubuntu files there? If not, what else do I do?
/dev/sda3: ntfs. W7 recovery partition. I don't want to be able to access this from Ubuntu. Leave it alone?

Device for boot loader installation I have set to /dev/sda; this will make it so Grub (with all boot options including Ubuntu 13.10 and W7) is started whenever I turn the machine on, right?

So in short my three questions:
How do I tell this thing where to install Ubuntu? Is it enough to have the partition I want set to "Use as: Ext 4 journaling file system" with mount point / ?
What do I need to do so Ubuntu will be able to read from and write to the Windows 7 partition sda2 while leavig the Windows 7 install alone during Ubuntu's install process?
What should I set "Device for boot loader installation" to if I want Grub as the startup screen?

Sorry that got a bit long; TIA for any answers!

---

### Post by grahammechanical on 2013-12-19
You are mostly right. Let us confirm.  I guess that Ubuntu 11.10 is on sda6 - 100GB. Right and that is where you want to install 13.10? 

So choose the Something else option and at the partitioning screen select sda6 and click Change. A dialog will appear. Select to use as Ext4. Tick the format the partition box. Give the partition a mount point of / and click OK. When back at the partitioning screen make sure that the device to install the boot loader on is set for sda. It usually is the default and click Install now. And pray :) It always makes me nervous. Even though I have done this many times.

Just make sure that you are installing into sda6. The installer will automatically use sda5 as swap. Ubuntu should be able to read/write to NTFS file systems. So, I think that you got it right.

Regards.

---

### Post by leon.buikstra on 2013-12-19
Okay, so the important bits are in place then. I guess I'll just try installing like this now; if I can't read from the W7 partition from Ubuntu I can always look for a way to fix that later. Thanks for the help!

Edit: in case anyone wondered, yes, Ubuntu will recognize any other partitions without having them marked for anything during installation.

---

