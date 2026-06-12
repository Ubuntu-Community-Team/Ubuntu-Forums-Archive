---
title: "Weird Windows install causing dual boot quandary"
date: 2010-06-25
forum: Installation &amp; Upgrades
---

### Post by quixote on 2010-06-25
I just bought a Fujitsu S760 with Win7 on it.  I need it for testing purposes, but for everything else I use ubuntu.  So I need a functioning copy of that Win 7.  The problem is, they've spread it in 4 partitions all over the drive, and I don't know whether I can move any of that stuff around without blowing it up.

Here's the setup (all ntfs of course):```

sda1    16GB  (8 used)    winOS files        hidden partition...
sda2    200mb             boot
sda3    150GB (12 used)   winOS, program, and user files
sda4    150GB (3 used)    some kind of recovery partition.    

```
So, unless I move something, all 4 primary partitions are already used, and I can't even make an extended partition for my linuxOS. :evil:

Plus, I like playing around trying to make hackintoshes, and that would take a primary partition too.

And one more thing: on first boot, the Win7 talks to the mothership and completes its installation.  So far, I've only used the machine with an ubuntu livecd (looks like everything works, btw), and I don't know how the drive will look once the Win7 is actually functional.

So, does anybody have any experience on what to do with this mess?  Can I just dump that recovery partition?  Unhide sda1, move boot there, ultimately make it bigger, and move the rest of the Win7 stuff there?  Somehow, I doubt it.  I know Windows checks for uuid (and MAC data??) to make sure it wasn't moved, so I haven't dared touch anything.

Unless a kind soul knows what I can do here, this otherwise fine laptop is going back! :mad:

---

### Post by pricetech on 2010-06-25
Your positive all 4 partitions are primary ??

Did you get install media with the computer ??  If not, I'd send it back anyway.  Media is cheap and if the manufacturer won't include it, that's just lame.

If you do have install media, you should be able to fix anything you break by partitioning for Ubuntu.  I'd wipe all 4 partitions with the live CD, then put windows 7 on a single partition taking up about half the drive.

---

### Post by quixote on 2010-06-25
I'm pretty sure they're all primary.  I looked at the drive with gparted, and it lists logical partitions under the extended one they belong to.  (Right?)  There's no extended partition, so I assumed they were all primary.

As for installation media, man oh man, the last time I got an honest-to-god Windows install disk with a computer was sometime in the last century.  This has a Recovery CD and "Drivers & Utilities".  I was under the impression those wouldn't reinstall the OS to a clean drive.  Wrong?

I was going to put Win7 in about 50GB.  It's not getting half my spiffy 7200rpm new drive.

---

