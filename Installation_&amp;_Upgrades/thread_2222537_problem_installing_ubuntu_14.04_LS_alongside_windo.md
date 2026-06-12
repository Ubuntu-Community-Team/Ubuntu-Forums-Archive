---
title: "problem installing ubuntu 14.04 LS alongside windows 7"
date: 2014-05-07
forum: Installation &amp; Upgrades
---

### Post by michael149 on 2014-05-07
Hello, this is my first message in this forum :)
I had windows 7 and i've decided that i want to install ubuntu alongside my windows 7.
Since ubuntus install didn't recognized windows 7 boot, i partitioned, gave 30 gb for ubuntu and installed it, after finishing the installation i've tried opening windows 7
but the boot just won't start. I tried inserting the windows 7 recovry disc and all i got was an error stating: "This version of System recovery is not compatible with the version windows... 
what can i do? I know i should somehow get into cmd and type bootrec.exe/FixMbr  and etc. but how can i get there? i would like to fix it without re-installing windows.
Thank you

---

### Post by mastablasta on 2014-05-07
how was ubuntu installed (did you maybe use wubi?)? does ubuntu work?

you could try another recovery disk

---

### Post by michael149 on 2014-05-07
i don't know what is wubi... Yes the ubuntu works, i am currently using it.
i tried several recovery discs nothing works, but the recovery disk built-in on my laptop was erased..

---

### Post by rev_jtsr on 2014-05-07
I found this [http://ubuntuforums.org/showthread.php?t=2206789](http://ubuntuforums.org/showthread.php?t=2206789).     This happened to me when I installed W8 on same drive as W7, you will have to install boot sector

---

### Post by Mark Phelps on 2014-05-07
How did you obtain 30GB of space -- by shrinking the Win7 OS partition? And if so, HOW did you do that shrinking -- by using GParted or the Ubuntu installer?

If the answer to yes is both, then you most likely corrupted the Windows filesystem by shrinking the OS partition with a non-Windows-filesystem tool.  Using fixmbr is not going to repair that because the MBR is outside the Win7 partition.  You have to run CHKDSK on the Win7 partition to repair it.

My suggestion is to download and burn a CD from the Minitool Partition Wizard Boot CD, boot from that CD, and use the option to Check the Windows OS partition.  That should fix it.  IF it still won't boot, you will have to make other repairs to the Win7 boot loader.

---

