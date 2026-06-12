---
title: "XP hibernate kills GRUB?"
date: 2008-06-28
forum: Installation &amp; Upgrades
---

### Post by icogs on 2008-06-28
I just installed Ubuntu (Hardy Heron) for the first time yesterday and it seemed to go OK except:-

dual boot is important to me as I need Windows XP for my work, so one of the first things I tried was quitting, booting into Windows, quitting, booting ubuntu etc. etc. When I tried hibernating Windows (something I do often when in the middle of stuff as it leaves stuff set up on the desktop. It's also way faster) GRUB failed to load with Error 17.

My question is; was it my hibernating windows which trashed GRUB, or just coincidence? I am a little wary of experimenting too much as it was a real pig to fix.

---

### Post by Partyboi2 on 2008-06-28
I have had this problem in the past when hibernating windows then booting into ubuntu. I was able to boot back into ubuntu by doing a clean shutdown of windows.

---

### Post by Aearenda on 2008-06-28
It is certainly unwise to hibernate on a dual-boot system, unless you can be absolutely sure that the non-hibernated OS will not touch the hibernated OS's filesystem(s) at all. Ubuntu will mount an NTFS partition by default on a dual boot system, so does not qualify. 

The reason is that the hibernated system has a frozen in-memory-but-hibernated understanding of what is going on in the filesystem, and if the disk does not match when the OS resumes, the disk could become corrupt.

Having said that, I haven't heard of this happening to Grub during the hibernate process.

---

### Post by icogs on 2008-06-29
Found out what was causing the problem, though not necessarily the solution.

The problem was when I looked, out of curiosity, at the disk partition structure with Partition Magic 8.0. PM objected to the partitions ubuntu's installation had created and helpfully "fixed" the problem without asking, effectively trashing the installation and doing something silly with one of my NTFS partitions (luckily causing no irrecoverable damage).

I don't know if the problem was brought about by the particular way I had the drive partitioned originally, but I am going to get a second drive and simplify everything before trying again.

---

