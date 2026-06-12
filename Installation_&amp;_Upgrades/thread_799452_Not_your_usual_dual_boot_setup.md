---
title: "Not your usual dual boot setup"
date: 2008-05-19
forum: Installation &amp; Upgrades
---

### Post by gmilne on 2008-05-19
I have 2 80G drives and 2X400G drives.
1 80G drive has XP and I would like to install Ubuntu 8.04 on the other 80G

When I try to boot from the disk I get the following message

[B]Buffer I/O error on device sr0 logical block32
Buffer I/O error on device sr0 logical block33
Buffer I/O error on device sr0 logical block32
Buffer I/O error on device sr0 logical block33 (*last 2 digits in line keep alternating.)*

BusyBox V1.1.3 (Debian 1:1.1.3  5Ubuntu12 Built in shell (ash[/B]
(initransfs)

All this on a DOS type black screen. I can get help but don't understand the commands offered. Should I be hitting F8 or ESC as  Ubuntu is trying to load? If so, what do I do then?

The blank 80G disk I'm trying to put Ubuntu on has been formatted NTFS

Any help most welcome. I think I'll also need advice with partitioning.

Thanks muchly.

---

### Post by galileon on 2008-05-19
sounds like a badly burnt disk to me, reboot, and try the option to check the install media. that should fail...

try to burn on lowest speed possible if thats the case...

---

### Post by gmilne on 2008-05-19
How can I install Ubuntu to Drive E:\. (I have several fixed drives.) I think it keeps trying to install itself to C:\ and C:\ is my storage drive. 
My Windows boot drive is F:\ 
and the blank drive to which I want to install Ubuntu - as dual boot) is E:

---

### Post by gmilne on 2008-05-19
> **galileon said:**
> sounds like a badly burnt disk to me, reboot, and try the option to check the install media. that should fail...

try to burn on lowest speed possible if thats the case...

Thanks - would you know how to answer my last post? I checked the integrity of my CD and it's fine.

---

### Post by jtrindle on 2008-05-19
When you get to the partitioning menu in the installer, does it list multiple drives under "Guided Partitioning"?  If so, there should be radio buttons next to each drive which allow you to select which one to use.  

If you really have four physical drives (not in a RAID), then E: would be the third one.  I find it odd that you say your windows boot drive is F:, what's on C: and D:?

If you don't see multiple drives under "Guided Partitioning", you might have to go through manual partitioning.  If the partitioner can't detect all your drives (I've heard some SATA setups have that problem) then we have a bigger issue.

---

### Post by galileon on 2008-05-19
there's usually an option during installation,where you choose "manual partition", "automatic partition", "some other option i cant remember", so that's probably where you would try to go "manual" and choose the appropriate drive...

that's from the hard boot install, not thw install from windows. are u using wubi? I have no experience with that (i don't go near a windoze machine without a hazmat suit anymore)

---

### Post by gmilne on 2008-05-19
LOL thanks - neither will I once I get this done. I'll try again.
/g

---

### Post by gmilne on 2008-05-19
Thanks. 
When I try to boot from the CD (checked for integrity)I get the following message

Buffer I/O error on device sr0 logical block32
Buffer I/O error on device sr0 logical block33
Buffer I/O error on device sr0 logical block32
Buffer I/O error on device sr0 logical block33 (last 2 digits in line keep alternating.)

BusyBox V1.1.3 (Debian 1:1.1.3 5Ubuntu12 Built in shell (ash
(initransfs)

All this on a DOS type black screen. I can get help but don't understand the commands offered. Should I be hitting F8 or ESC as Ubuntu is trying to load? If so, what do I do then?

C: and D: I use for data storage. I boot XP from F: and install XP programs in F:\Program Files

I don't know why the drives are named that way. and I don't get to the paritioning menu. Next step?
=========================================================

> **jtrindle said:**
> When you get to the partitioning menu in the installer, does it list multiple drives under "Guided Partitioning"?  If so, there should be radio buttons next to each drive which allow you to select which one to use.  

If you really have four physical drives (not in a RAID), then E: would be the third one.  I find it odd that you say your windows boot drive is F:, what's on C: and D:?

If you don't see multiple drives under "Guided Partitioning", you might have to go through manual partitioning.  If the partitioner can't detect all your drives (I've heard some SATA setups have that problem) then we have a bigger issue.

---

### Post by gmilne on 2008-05-19
Thanks - I managed to install 7.1 and the GRUB but on selecting Ubuntu I get the initranfs message. Can you tell me what to do about this? Thanks

---

