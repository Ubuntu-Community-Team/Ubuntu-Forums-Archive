---
title: "Drive Rescue (dd_rescue?)"
date: 2007-06-05
forum: Installation &amp; Upgrades
---

### Post by Waiting4nAngel on 2007-06-05
Okay, here's my problem in summary;

Basically, I've used Yellowdog Linux for 2 years total, after a short year-long break of mac-dedication, I decided to try out Ubuntu from my friend's cd. We booted into the cd on my Mac Mini Intel, after partitioning it into the basic setup for dual boot: EFI, Mac OS X, Linux Root, Home, and Linux Swap. After partitioning it, for some reason my EFI boot partition is not being read, and Ubuntu will not install as a recognized boot-partition. Due to this, my only access to the internet is through the Ubuntu boot-cd.

I have a 250gb external drive, with about 60gbs of music that I collect, along with a few other backed up programs and utilities for Mac. So there's about 156gb left on the drive which only has 1 HFS+ partition.

I cannot boot into my Mac OS X partition to save any of my files, and was looking around for possible solutions.

Am I right in thinking that dd_rescue is the best solution here? I would have to copy the 50gb Mac OS X block to my external drive, however my question is; will it safely copy the block to the drive WITHOUT erasing or corrupting any of my music-collection? it's 60gb of music, I don't wanna lose it.

If that won't work, what's my best bet? Are there any other solutions anyone can think of?

Basically, None of the partitions on my internal drive are currently bootable, and my external drive has only 1 partition which I cannot risk losing, or damaging.

I need to rescue my Mac OS X block, since I wasn't really thinking this sort of problem would arise, I didn't back up any of the files on it.

If anyone can help, I'd really appreciate it.
Thanx,
Cory Armstrong

---

### Post by Waiting4nAngel on 2007-06-06
Is there anyone that's able to help me? Even if you can just let me know that my stuff is okay... if I know there's no way to get the data back then I'll just reformat my whole drive and start from scratch, but I'd like to know if it's worth rescuing.

Thanx,
Cory Armstrong

---

### Post by confused57 on 2007-06-06
A Google search found this method of mounting your hard drive, using the live cd:
[http://jclark.org/weblog/2005/05/24/ubuntumount/](http://jclark.org/weblog/2005/05/24/ubuntumount/)

You should be able to drag & drop data files from your internal hard drive to your external drive.

---

