---
title: "[SOLVED] Install freezes at partitioning."
date: 2008-01-23
forum: Installation &amp; Upgrades
---

### Post by someonestolemyname on 2008-01-23
I am trying to install a command-line system from the Ubuntu alternate cd. I've already set up Xubuntu 7.10 on this computer successfully, although with a different hard drive.

The install goes fine until I get to partitioning. The screen that shows 'Preparing for partitioning (or something like that)' shows, then it blanks (blue with the gray bottom bar) in preperation for the next step. That step never happens, it just sits there. I can type into the gray bar, but the install stops. I have to exit via ctr-alt-del.

The hard drive has a screwed up windows install. Literally, the windows install was unsuccessful and is in the middle of it. Could that be causing a problem? The working Xubuntu install can't mount the drive because it is locked.

Other than that, it is an identical install to one I did a few days ago (that worked perfectly.)

I did check the cd for errors, it was fine. It is my second cd. The first was bad, although it stopped at the same spot. That makes me think that the hard drive or other hardware is the problem. Could ubuntu not just wipe the drive? Or does it have to be properly mounted to repartition?

System Information:

Old Gateway computer
Pentium 4 1.8 Ghz
128mb of ram
20 gb hard drive - w/ botched windows install.
2 cd burners

I can answer any more questions as well.

btw, the bad windows install was because I wanted to see if I could get Windows XP to run on that low of specs, specifically the 128 mb ram. It does (although it tooom a couple of tries, and runs far slower than the Xubuntu system with comparable features, and more awesomeness.)

If anyone can help, thanks.

---

### Post by someonestolemyname on 2008-01-23
As an update, I just tried with the other hard drive. I've installed Xubuntu on this exact computer befor with no problems.

I'm reburning the disk, which verifies, again to make sure that is not the problem.

---

### Post by 565Customz on 2008-01-23
i cant get eh partitioning to work on mine either...i think maybe its the software...

---

### Post by Partyboi2 on 2008-01-23
try using something like [dban]("http://dban.sourceforge.net/") to wipe the hard drive clean then try installing again.

---

### Post by someonestolemyname on 2008-01-23
Ok, well I let ikt sit, and eventually the screen came up. The reason for my problems is that I had my external hard drive plugged in, which apparently took forever to examine (250gb, 3 NTFS partitions...).

Once I removed it, the partitioning went perfectly.

My own stupidity triumphs despite hundreds of bug-checkers yet again...

---

