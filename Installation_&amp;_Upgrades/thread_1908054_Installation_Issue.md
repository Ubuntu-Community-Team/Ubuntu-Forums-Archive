---
title: "Installation Issue"
date: 2012-01-12
forum: Installation &amp; Upgrades
---

### Post by Furler on 2012-01-12
I've tried to get this resolved on the Linux Mint forum but no one could really tell me what to do, so I thought I would give it a chance here. I assume I would get the same error if I tried installing Ubuntu. If not, I will try and install it instead.

The error I am receiving:
[http://i.imgur.com/Np7ie.jpg](http://i.imgur.com/Np7ie.jpg)

More  detail:
[http://i.imgur.com/2xov0.png](http://i.imgur.com/2xov0.png)
(It's  showing me as having a striped 1tB HD but I told it not to use a raid  array in my BIOS).

BIOS #1:
[http://i.imgur.com/OgVzr.jpg](http://i.imgur.com/OgVzr.jpg)

BIOS  #2:
[http://i.imgur.com/28Wyb.jpg](http://i.imgur.com/28Wyb.jpg)

BIOS  #3:
[http://i.imgur.com/VL37M.jpg](http://i.imgur.com/VL37M.jpg)

My  RAID is disabled, right? So why is it showing that I don't have two 500gB HD's?

---

### Post by spacecheck on 2012-01-12
Did you buy the SATA HDDs new or get them used? Do you know if there was once a raid installed on one or both of the drives?

I read in a recent post, that sometimes a drive will retain the raid information until forced to relese it. I'll look for it and add it when I find it.

The other thought is that it (the mint installation) is asking you if it should create a software raid using both disks. That's the marked option in your first screenshot. The option to use both drives appears to be the first, not selected option...

Good luck!

---

### Post by Furler on 2012-01-12
> **spacecheck said:**
> Did you buy the SATA HDDs new or get them used? Do you know if there was once a raid installed on one or both of the drives?

I read in a recent post, that sometimes a drive will retain the raid information until forced to relese it. I'll look for it and add it when I find it.

The other thought is that it (the mint installation) is asking you if it should create a software raid using both disks. That's the marked option in your first screenshot. The option to use both drives appears to be the first, not selected option...

Good luck!

It use to be set up as Raid 0 because I was using Windows 7, how do I force it to release?

---

### Post by spacecheck on 2012-01-12
According to this post:

[http://ubuntuforums.org/showthread.php?t=1324025&page=2](http://ubuntuforums.org/showthread.php?t=1324025&page=2)

You would run:

```
sudo apt-get remove dmraid
```

If it works please mark the thread as [Solved]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads").  
Good luck!

---

### Post by darkod on 2012-01-12
Boot ubuntu in live mode with the cd and in terminal run:

sudo dmraid -E -r /dev/sda

Replace /dev/sda with the correct disk name(s), like /dev/sdb, /dev/sdc, etc. Do this on all disks you want to remove the raid meta data from.

---

### Post by darkod on 2012-01-12
> **spacecheck said:**
> According to this post:

[http://ubuntuforums.org/showthread.php?t=1324025&page=2](http://ubuntuforums.org/showthread.php?t=1324025&page=2)

You would run:

```
sudo apt-get remove dmraid
```

No, that just removes the dmraid package temporarily from the live mode. The meta data will remain unless removed as posted above.

While it might allow you to install with simply removing the package, the existing meta data will become a problem sooner or later.

---

### Post by Furler on 2012-01-12
> **spacecheck said:**
> According to this post:

[http://ubuntuforums.org/showthread.php?t=1324025&page=2](http://ubuntuforums.org/showthread.php?t=1324025&page=2)

You would run:

```
sudo apt-get remove dmraid
```

I'm slowly getting there, it's now showing up as two 500gB HD's, clcked to install it on one and got "The ext4 file system creation in partition #1 of SCSI6 (0,0,0) (sda) failed."

---

### Post by spacecheck on 2012-01-12
See darkod's forgoing [post]("http://ubuntuforums.org/showpost.php?p=11606476&postcount=5").

If it works please mark the thread as [Solved]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads").  

Good luck!

---

### Post by Furler on 2012-01-12
> **spacecheck said:**
> See darkod's forgoing [post]("http://ubuntuforums.org/showpost.php?p=11606476&postcount=5").

If it works please mark the thread as [Solved]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads").  

Good luck!

Thank you all so much, worked great! :D

---

