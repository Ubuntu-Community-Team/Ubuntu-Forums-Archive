---
title: "Problem installing Ubuntu 11.10"
date: 2011-10-24
forum: Installation &amp; Upgrades
---

### Post by demoltionman427 on 2011-10-24
I've tried both 64 and 32 bit. My computer is 64 bit. Running windows 7. I'll attach my screenshot to show you guys the error. I would greatly appreciate any help!

---

### Post by demoltionman427 on 2011-10-24
Please PM me if you are willing to walk me through the process because it's not working for me.

---

### Post by yo_bhan on 2011-10-24
Why not install dual boot like usually, not wuby.
T think, wubi have problem for most user

maybe this [link]("http://ubuntuforums.org/ubuntuforums.org/showthread.php?t=1639198") will help, talk about wubi

---

### Post by bcbc on 2011-10-25
You've likely got dynamic disks (or windows is not allowing you to boot from whatever A: is). Dynamic disks are not supported by linux. You have to remove them before setting up a dual boot with Ubuntu (wubi or other).

---

### Post by Mark Phelps on 2011-10-25
If you're going to dual-boot, and you're currently running Win7 on your PC, then you need to do the following: Confirm that you don't already have the 4 Primary partition limit.  To do this, open the Win7 Disk Management utility and count the number of "drives" (that's what Windows calls partitions).  If you already have 4, then you're going to be faced with a LOT of work because you will have to remove one before you can create another for Ubuntu.

Also, check the "drive" types and confirm they are NOT Dynamic Disks.  Ubuntu can't be installed when Dynamic Disks are being used.

If you decide to go ahead with dual-boot, then do the following:
1) Use only the Win7 Disk Management utility to shrink your Win7 OS partition to make room for Ubuntu. Do NOT use the Ubuntu installer to do this. If you already have 4 partitions in Win7, do NOT allow the partitioner to create another partition.  This will convert your partitions into Dynamic Disks -- effectively preventing the installation of Ubuntu and causing you further problems.
2) Once you have Win7 shrunk, use the Win7 Backup feature to create and burn a Win7 Repair CD. This will come in handy later, should you need to repair your Win7 boot loader from the dual boot setup.

---

