---
title: "Manual Grub Install? (or alternatively Wubi with &gt;30 GB?)"
date: 2010-08-30
forum: Installation &amp; Upgrades
---

### Post by butsam on 2010-08-30
I tried installing Ubuntu on a machine with 2 TB of disk space, wanting it to be 1/2 Ubuntu and 1/2 Windows Vista. So, I shrank the Partition to be 1 TB Win and 1 TB Free, then installed Ubuntu.

At the very end, I got an error that it couldn't install grub! It complained about not finding /dev/sda. I tried selecting each drive entry on the list and they all failed saying they couldn't find /dev/sda. The drives are RAID, which I hear may be part of the problem. So, now I have Ubuntu installed but I just can't get to it.

My question is, how can I get to Ubuntu? I'll take any solution right now. Can Wubi be used to simply edit the Windows boot loader to add a boot for Ubuntu? Can I just nuke my previous installation and use Wubi to install Ubuntu on 1 TB of the drive? (I saw no option for this -- it looked like the largest size I could select was 30 GB. Can I select more than 30 GB?) Should I resort to installing Grub manually?

Please help!

---

### Post by oldfred on 2010-08-30
I do not know RAID but here is another thread.

[http://ubuntuforums.org/showthread.php?t=1469169](http://ubuntuforums.org/showthread.php?t=1469169)

---

### Post by bcbc on 2010-08-30
> **butsam said:**
> I tried installing Ubuntu on a machine with 2 TB of disk space, wanting it to be 1/2 Ubuntu and 1/2 Windows Vista. So, I shrank the Partition to be 1 TB Win and 1 TB Free, then installed Ubuntu.

At the very end, I got an error that it couldn't install grub! It complained about not finding /dev/sda. I tried selecting each drive entry on the list and they all failed saying they couldn't find /dev/sda. The drives are RAID, which I hear may be part of the problem. So, now I have Ubuntu installed but I just can't get to it.

My question is, how can I get to Ubuntu? I'll take any solution right now. Can Wubi be used to simply edit the Windows boot loader to add a boot for Ubuntu? Can I just nuke my previous installation and use Wubi to install Ubuntu on 1 TB of the drive? (I saw no option for this -- it looked like the largest size I could select was 30 GB. Can I select more than 30 GB?) Should I resort to installing Grub manually?

Please help!

Don't use wubi for this. You can use the entire drive with a normal install. Wubi is suitable for smaller installs when partitioning is an issue - this is not the case for you.

Edit: see [this]("https://wiki.ubuntu.com/LucidLynx/ReleaseNotes#Dmraid active by default on Desktop CD") as well. Might apply.

---

