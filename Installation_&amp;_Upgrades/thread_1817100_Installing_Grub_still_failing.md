---
title: "Installing Grub still failing"
date: 2011-08-02
forum: Installation &amp; Upgrades
---

### Post by FormatSeize on 2011-08-02
This is the second time this has happened. I wouldn't be upset if it failed during an earlier part of the installation. Installations are boring. I posted this the first time that it happened, but I think that wasn't the correct forum for that. 

Anyhow, I didn't immediately give up on this today. I'm still here on the live CD, and completely unexciting things are still going on. The error I get involves a popup window, which says:
"Exectuing 'grub-install /dev/sda' failed.
"This is a fatal error."

I think what I am seeing is attached to this post. I've never had installation problems. I'm even self taught on how to burn an iso, so this is all new to me. 

I go into a terminal and type try to use cfdisk, and it tells me:
```
FATAL ERROR: Bad primary partition 1: Partition ends after end of disk
```
This isn't the first time that cfdisk yelled at me about something that sounded impossible to be true in the first place so I just ignored it, but this time it bothers me. My setup is different. I've always done installs on a single disk. This time, it's three clean disks set up in a RAID 5. Yes, I did Google "RAID" before I did this, but the only real reason I did it is because a buddy of mine was talking about it and it sounded cool. Not really because I need one, or that I even fully understand why it's good to have one. It probably has nothing to do with my problem, but I'm just throwing that variable out there. 

Thanks.

EDIT: More unexciting news. When I use fdisk to look for what my partition table could look like, I can't find /dev/sda. There's only /dev/sdb1 which is bootable, and /dev/sdc, which doesn't show a device, Boot, Start, End, Blocks, Id, or system. I don't know if that helps or hurts, but I'm confused. 

Could it be that there isn't an /dev/sda for the grub-install command to find?

---

### Post by FormatSeize on 2011-08-02
Update: I took the disks out of RAID, and tried to install on a single 250 GB hard drive. The same thing happened.

---

### Post by Bucky Ball on 2011-08-02
Is this happening before or after the partitioning section of the install?

---

### Post by FormatSeize on 2011-08-02
It is happening after the partitioning step. The installation will go all the way up through the "Copying Files", "Installing System", and the "Downloading language packs" (which takes a long time), and after configuring apt and configuring bootloader (at around the 66% complete mark) is when I get the grub-install error.

EDIT: Well, things just got interesting. The same error just happened with Kubuntu 11.04.

---

### Post by FormatSeize on 2011-08-02
Here's what I've done so far:

1. Tried to install 11.10 on the RAID 5. Nothing.
2. Tried 11.04 on the RAID 5. Still get the same error. 
3. Dismantled the RAID, and tried to install on only one hard disk. Nothing.
4. I realized that the disk I was installing on was called "/dev/sdc". Grub seems to be looking for a "/dev/sda". So I rebooted and picked the disk that the installer is calling "/dev/sda", and I am almost to the point where the installation fails right now.

I'll keep you posted.

EDIT: For me, installing on a single disk that the installer calls "/dev/sda" works with no problem. It got past that, ran update grub, and seems to be going well. 

Would this be something that I should report? I find it strange that the installer looks for a specific disk name. I'm sure everyone isn't as willing as I am to destroy RAIDs and repeatedly clear several disks of data several times until they accomplish an install on the fifth try.

---

### Post by YannBuntu on 2011-08-03
> **FormatSeize said:**
> Would this be something that I should report?

yes, you should report it on Launchpad.

---

