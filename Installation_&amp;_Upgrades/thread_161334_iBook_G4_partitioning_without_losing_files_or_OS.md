---
title: "iBook G4 partitioning without losing files or OS?"
date: 2006-04-16
forum: Installation &amp; Upgrades
---

### Post by NodlezFodlez on 2006-04-16
Hi. I'm trying to install ubuntu, but when I got to the partition screen, I wasn't sure what to do. (as geeky as I am, i've never had to partition a disk :( ) So I went to the mac disk utility, but when scanning the help file (wondering what another function is) I noticed that it said that you can't partition the disk without losing all of your files.

So...

Is there a way to partition the disk without losing my many files or the OS? Backing up my 10GB of files wouldn't be easy, but it would be doable, but I don't know about the OS.

Has anyone done this succesfully?

---

### Post by aysiu on 2006-04-16
This may help:
[https://wiki.ubuntu.com/Installation/PowerPC](https://wiki.ubuntu.com/Installation/PowerPC)

---

### Post by NodlezFodlez on 2006-04-16
that doesn't exactly help... because my problem is that I already had went into "manually partition" because the free space partitioner didn't work, and found that it was because of the 27.9GB hard drive, 27.8GB was being used by partition #3 as my Mac OS X hard drive, and I couldn't change the size down!

EDIT: I forgot to mention (this should be obvious) that the free space partitioner didn't work because it said "insufficiant free space"... Duh, there was approx 135MB

---

### Post by aysiu on 2006-04-16
I believe when it says there's insufficient free space, it's actually talking about unused space and not unpartitioned space. So even if Mac OS X takes up the whole drive, if there's empty space, it should automatically resize the partition and create a new one.

You can manually resize, too.

This *may* help you--I'm not sure because it's tailored to a Windows dual boot, but I believe the same resizing principles should apply:
[http://users.bigpond.net.au/hermanzone](http://users.bigpond.net.au/hermanzone)

I'm sorry I can't be more help. I've never done a PowerPC dual boot, and the documentation for it is scarce.

---

### Post by linear on 2006-04-16
There's a thread [here]("http://ubuntuforums.org/showthread.php?t=89960") on using **parted** to resize an HFS+ partition. You really ought to back everything up anyway, just in case...

---

### Post by NodlezFodlez on 2006-04-16
yeah that looks like it would work...

but should I back up 10-15 GB of files? I have a dell with a 250GB hard drive, maybe I could hook that up through an ethernet cable and copy/move the files overnight.

---

