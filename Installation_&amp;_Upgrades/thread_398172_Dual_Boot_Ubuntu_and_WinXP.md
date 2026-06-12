---
title: "Dual Boot Ubuntu and WinXP"
date: 2007-03-31
forum: Installation &amp; Upgrades
---

### Post by SNYP40A1 on 2007-03-31
I started yesterday with 2 hard drives.  I backed up all my important stuff on the second hard drive.  On the first hard drive which had WInXP on NTFS partition, I installed Ubuntu 7.04 (yes, beta I know -- but I heard it was more WInXP dual boot friendly).  Ubuntu made my system such that nothing loaded.  After boot, it would give an operating system missing message.  I booted Ubuntu Live CD and could still see all my WInXP and Ubuntu files.  Someone tried helping me get GParted working last night and after wiping off the WInXP partition, I created a new NTFS partition, extended partition holding both ext3 and a linux swap space (~27 GB / 1 GB).  Then I installed Ubuntu on those two extended partitions.  Install went fine, but when I rebooted the PC off hard drive, nothing loaded.  So I reinstalled WinXP on the NTFS partition this morning.  After installing XP I got a NTLDR missing error.  I found a quick fix on the internet involving copying ntldr and ntdetect.com into the root C: dir.  XP now loads fine (although I see a brief error flash by right as it is accessing the boot loader, but it somehow fixes it self and boots properly).  However, I also have Ubuntu on the extended partition that I cannot access.  What do I need to do to dual boot?  I like Ubuntu so far, but there really needs to be an easier way to setup dual boot Win / Linux.  I have been interested in Linux for the past 8 years and this is the first time I have installed it (used Knoppix for a while to reconfig HD).  Some people such as myself need both operating systems and there should be a way to upgrade without hosing windows.  Please help.

---

### Post by zvacet on 2007-04-01
[http://ubuntuforums.org/showthread.php?t=179902&highlight=two+hard+drives]("http://ubuntuforums.org/showthread.php?t=179902&highlight=two+hard+drives")

---

