---
title: "Grub stage 1.5 help?"
date: 2006-07-29
forum: Installation &amp; Upgrades
---

### Post by nwillis on 2006-07-29
Hi; I've been beating my head against this problem all day, and getting nowhere.  Here's the situation: I have an amd64 machine with a working installation of dapper on a lone sata disk.  I'm installing i386 dapper on a separate ide disk (in order to test out sagetv, which is binary 386-only).  The sata disk un unhooked and unpowered.

The lone ide disk is secondary master (cd drive is primary master, a zip250 is primary slave).  I can install fine, but booting fails right after bios with "grub loading stage1.5read error" -- which hangs.  Nothing, absolutely nothing I have tried will fix this.

I downloaded the "alternate" CD image, booted into rescue mode, chose the re-install grub option -- no difference.

I tried the "text mode" install, which this page([http://doc.gwos.org/index.php/Restore_Grub](http://doc.gwos.org/index.php/Restore_Grub)) said would let me drop out at the manual partition stage and choose reinstall grub -- it did, but it made no difference.

I found this thread: [http://ubuntuforums.org/showthread.php?t=75648](http://ubuntuforums.org/showthread.php?t=75648) which sounds like the same situation, but does not have an answer.  I changed the boot sequence, and it did not make a difference.

I found one other thread: [http://ubuntuforums.org/showthread.php?t=190059](http://ubuntuforums.org/showthread.php?t=190059) and nobody even had a reply.

Please help?  Everything I have found searching on the web has real specific references to drive ids and partitions, and none of them seem to translate to mine.  For the record, the installer choose to partition the entire drive, first partition ext3, then a logical partition, inside which is one partition for swap.

Any help at all?  This is a grub nightmare.

---

### Post by Soarer on 2006-07-29
I believe I had a similar problem. See the thread at: [http://www.ubuntuforums.org/showthread.php?t=158504](http://www.ubuntuforums.org/showthread.php?t=158504)

Actually, I never fixed it with GRUB, but switched to LILO using Herman's instructions at: [http://www.users.bigpond.net.au/hermanzone/p12.htm#Install_Lilo_from_Breezy_Install_CD](http://www.users.bigpond.net.au/hermanzone/p12.htm#Install_Lilo_from_Breezy_Install_CD)

It has been working fine ever since. I have feeling I am unable to write to the MBR but I could (easily) be wrong.

---

