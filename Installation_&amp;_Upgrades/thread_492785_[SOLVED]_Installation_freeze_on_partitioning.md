---
title: "[SOLVED] Installation freeze on partitioning"
date: 2007-07-05
forum: Installation &amp; Upgrades
---

### Post by Riccardo63 on 2007-07-05
I'm a beginner.
The PC where i'm trying to install ubuntu is a
AMD Athlon XP 2200
RAM 256
MAxtor IDE 40 Gb
I've downloaded and burn ubuntu-7.04-desktop-i386.iso and  ubuntu-6.06.1-desktop-i386.iso.
After booting, the liveCD startcorrectly with both CD, then i try to install it on hard drive by icon on desktop.
With 7.04 is very slow but with 6.06 is faster.
But both version freeze when i start partition tool.
I've tried with all 3 options: auto partition and manual, but when i click forward it freeze with houglass cursor for several hours!!
I've also tried the "Check CD for defects" on boot: the cd is ok.
In the hard disk there was a Windows XP Pro installation. I've not formatted it before.

1 - what i'm mistaking?
2 - Is there another method to install ubuntu, without live CD?

---

### Post by lisati on 2007-07-05
1. I don't know  
2. On the official Ubuntu download site there's a check-box for the download of an "alternate" CD. It has a few more questions, and the display is text based, but it often works when the "Live CD" has problems

---

### Post by aquavitae on 2007-07-05
I see you have AMD, is it amd64 bit?  If so you should probably be using the livecd for the 64 bit architecture: ubuntu-7.04-desktop-x86_64.iso.  I don't know if this will solve your problem, because i386 (32bit) should work on 64, but it might make a difference.  Worth a try!

Does it freeze before of after you've set up the partitions?  I.e. does it freeze while you're creating the partitions or before you've specified the partition layout?  Hope you can make sense of that:D

---

### Post by Riccardo63 on 2007-07-05
No it is an AMD athlon XP 2200 32 bit.
It freeze after i've specified one of 3 partition method (Automatic, entire disk, manual)
But now i want to try with the *alternate* CD version as lisati says.

---

### Post by Riccardo63 on 2007-07-05
OK now i've installed the alternate version and it works.
Thanks a lot.

---

