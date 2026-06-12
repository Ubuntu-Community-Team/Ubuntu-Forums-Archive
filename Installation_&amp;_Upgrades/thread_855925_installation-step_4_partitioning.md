---
title: "installation-step 4 partitioning"
date: 2008-07-11
forum: Installation &amp; Upgrades
---

### Post by widespread on 2008-07-11
I'm trying to install xubuntu from a cd.  On step 4, I have to prepare disk space by partitioning the drive. No matter what option I choose (whether guided or manual), I get an error message saying "too small size."  What does this mean, and how do I fix it?  My hd drive is 80 gb.  Thanks for the help.

---

### Post by widespread on 2008-07-11
the step finally went through, but now it is trying to partition the drive, but nothing is happening.  MY computer is stuck on zero percent for a long time.

---

### Post by VMC on 2008-07-11
> **widespread said:**
> I'm trying to install xubuntu from a cd.  On step 4, I have to prepare disk space by partitioning the drive. No matter what option I choose (whether guided or manual), I get an error message saying "too small size."  What does this mean, and how do I fix it?  My hd drive is 80 gb.  Thanks for the help.

How much of the 80gb drive is used by another OS? IF your using windows , right-click on the drive and see how much free space is left.

---

### Post by widespread on 2008-07-11
> **VMC said:**
> How much of the 80gb drive is used by another OS? IF your using windows , right-click on the drive and see how much free space is left.

Windows uses about 28 gb.  So xubuntu had about 52 gb to install with.

---

### Post by Kevbert on 2008-07-11
> **widespread said:**
> I'm trying to install xubuntu from a cd.  On step 4, I have to prepare disk space by partitioning the drive. No matter what option I choose (whether guided or manual), I get an error message saying "too small size."  What does this mean, and how do I fix it?  My hd drive is 80 gb.  Thanks for the help.

I assume that your other OS is XP.  You may find you still have data towards the end of the disk. This is the windows paging (swap) file which may be causing the problem. If this block of data has not been moved when you defrag the drive, you'll need to turn off this file. It can be found at Control Panel - System - Advanced Tab. Now click on Settings under Performance and select the Advance Tab. Now click on Change, the Virtual Memory paging file and select the No Paging File radio button. No click on Set, OK, OK, OK and close Control Panel.
Reboot the machine and then defrag the hard disk again. There should now be extra room at the end of the disk.
Don't forget to back everything up and turn on the paging in windows once you've sorted out Ubuntu.
The other thing is how much memory (RAM) does your machine have ?   It may be that you don't have enough memory to run the graphical install and should go for the text based (alternate) install instead.

---

### Post by widespread on 2008-07-11
my computer has 512 MB of ram.  I guess I'll defrag windows and follow the directions you gave me.  Thanks for the help fellas.

---

### Post by aceupmysleeve on 2008-07-19
> **Kevbert said:**
> I assume that your other OS is XP.  You may find you still have data towards the end of the disk. This is the windows paging (swap) file which may be causing the problem. If this block of data has not been moved when you defrag the drive, you'll need to turn off this file. It can be found at Control Panel - System - Advanced Tab. Now click on Settings under Performance and select the Advance Tab. Now click on Change, the Virtual Memory paging file and select the No Paging File radio button. No click on Set, OK, OK, OK and close Control Panel.
Reboot the machine and then defrag the hard disk again. There should now be extra room at the end of the disk.
Don't forget to back everything up and turn on the paging in windows once you've sorted out Ubuntu.
The other thing is how much memory (RAM) does your machine have ?   It may be that you don't have enough memory to run the graphical install and should go for the text based (alternate) install instead.

I am having the same problem

I followed your advice, except now when I try and run the defrag this comes up:

C:\WINDOWS\system32\dfrg.msc

The paging file is too small for this operation to complete.

Same error when I try to launch firefox

*and* I can't open control panel to reverse the operation. I don't know if safe mode would help at all, I am yet to try, but can you help either more with the problem to do with installing xubuntu or with this new problem within XP...

Actually as I have been typing I have been trying the defrag again on my laptop (which is where these problems are occurring, thank goodness for owning far too many computers!) but although the program has opened it doesn't look as if it is actually defragmenting the disc... will keep you up to date with future developments. 

:confused:

[EDIT]: forgot to mention, I have 256 mb

---

### Post by aceupmysleeve on 2008-07-19
well, pressing defrag didn't help, just said it was unable to do it.

Im gonna try and install xubuntu now

will edit this post to let you know results

EDIT: It appears to be working but has stayed on 0% for ages - crashed?  Disc doesnt seem to be spinning either...

---

### Post by aceupmysleeve on 2008-07-19
hopeful bump... sorry to be so impatient

---

### Post by monkseatcheese on 2008-07-19
I have the same problem. i have 150 GB of free space on my harddrive, but half of the files are lumped at the end, even when i defrag. Im defragging again, and see what happens this time after i following kevberts instructions

---

### Post by aceupmysleeve on 2008-07-20
> **monkseatcheese said:**
> I have the same problem. i have 150 GB of free space on my harddrive, but half of the files are lumped at the end, even when i defrag. Im defragging again, and see what happens this time after i following kevberts instructions

It's been 12 hours since your post - whats happened? Unfortunately after I followed those instructions I was unable even to defrag, did this happen to you?

Although unable to defrag (or do anything really in XP) when I booted again from the disc and tried to install when it got to this stage it began to partition it (or so it said) but after about 2 hours it still said 0% and the disc had stopped spinning, and the computer appeared to have crashed...
No progress since then but did you experience something similar?

---

### Post by aceupmysleeve on 2008-07-21
bump...
Loads of new threads

---

