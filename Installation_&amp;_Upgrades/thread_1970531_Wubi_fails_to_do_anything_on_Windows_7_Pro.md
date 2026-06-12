---
title: "Wubi fails to do anything on Windows 7 Pro"
date: 2012-05-01
forum: Installation &amp; Upgrades
---

### Post by AlunB on 2012-05-01
I've been trying to install 12.04 on my Windows 7 64 bit machine, and have had no joy at all. Wubi just runs for a second or two and then I get dropped back to desktop. No processes, tasks or programs in Task Manager other than the usual at that point - certainly nothing Wubi related is showing up. I have turned off my antivirus, run Wubi as administrator, and it seems to be the only program I can't install! The PC is a fairly clean installation, and has no software on it that could be blocking the install.
 
I have tried running Wubi off the download CD, as well as from the download Wubi only .exe.
 
Anyone having similar issues or got any suggestions? I've browsed the forums, and people seem to be getting problems (if any), much later on in the install process.
 
Very frustrating, especially as I installed Mint with no issues a couple of weeks ago (now removed, with no traces left on the system).

---

### Post by darkod on 2012-05-01
And why don't you simply go with proper dual boot? It's much better than wubi anyway.

---

### Post by Mark Phelps on 2012-05-01
If you're going to dual-boot, and you're currently running Win7 on your PC, then you need to do the following: Confirm that you don't already have the 4 Primary partition limit.  To do this, open the Win7 Disk Management utility and count the number of "drives" (that's what Windows calls partitions).  If you already have 4, then you're going to be faced with a LOT of work because you will have to remove one before you can create another for Ubuntu.

Also, check the "drive" types and confirm they are NOT Dynamic Disks.  Ubuntu can't be installed when Dynamic Disks are being used.

If you decide to go ahead with dual-boot, then do the following:
1) Use only the Win7 Disk Management utility to shrink your Win7 OS partition to make room for Ubuntu. Do NOT use the Ubuntu installer to do this. If you already have 4 partitions in Win7, do NOT allow the partitioner to create another partition.  This will convert your partitions into Dynamic Disks -- effectively preventing the installation of Ubuntu and causing you further problems.
2) Once you have Win7 shrunk, use the Win7 Backup feature to create and burn a Win7 Repair CD. This will come in handy later, should you need to repair your Win7 boot loader from the dual boot setup.

---

### Post by AlunB on 2012-05-05
Thanks for the advice, but I really do not want anything other than a Wubi install on this particular PC.


My other machines are set up with various sorts  of dual-boot, or linux only, on THIS machine I want to figure out why Wubi just will not run - intellectual curiosity, and useful for then helping my various charities with any install issues.

So, any other clues woul be much appreciated!

---

