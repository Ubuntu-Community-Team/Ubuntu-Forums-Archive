---
title: "Dual boot installation, no auto-partition option"
date: 2008-07-12
forum: Installation &amp; Upgrades
---

### Post by monguin61 on 2008-07-12
I'm hoping someone can help me out with installing Ubuntu 8.04 on top of XP SP2 on my dell laptop. I cleared out 15GB of my 30GB hard drive, and defragmented it before attempting to install Ubuntu from a CD, but I'm having trouble partitioning. I have a beginners knowledge of using Linux and getting around on a running system, but I've never installed Linux or done basic configurations before, so I need kind of a lot of help.

When I get to step 4/7 of the installer (Prepare disk space), I only have two partitioning options: Guided - use entire disk (which I don't want to do) and Manual. As I understand it, the third option, Resize partition automatically, is missing. I want to use this option.

I have been searching online and it seems that I should be able to get that option by unmounting the windows partition before trying to install Ubuntu. I found this guide: [http://www.howtoadvice.com/ResizePartition](http://www.howtoadvice.com/ResizePartition) , but 
A) qtParted is not available in my Synaptic package manager,
B) gParted is available, but will not let me resize my partition (/dev/sda1),
C) the output of cat /proc/mounts does not include "/dev/sda1" at all.

If someone could help me through this process, I'd really appreciate it. I'm also willing to do the manual partition if I can't get the auto option to work, but I'll need just as much help setting that up as well.

For what its worth, I am missing the auto option on both my laptop, which has gone through multiple XP reinstalls, and my new desktop, which is running its first fresh XP install, but also has more than one HDD.

Thanks for any help.

---

### Post by SkonesMickLoud on 2008-07-12
GParted can only read NTFS partitions.  It cannot grow, shrink, or even create an NTFS partition.

I've never used the guided partitioner, but it sounds like this is the problem.  What you'll have to do is use the partitioner on the Windows XP disk to shrink your existing XP partition, and create a new one.  You don't have to worry about giving the new partition a FS, as the Ubuntu installer will do that for you.  However, if Windows forces you to create one, choose either of the FAT's or ext3/2.  Doesn't matter which as Ubuntu will be able to modify either of those.

After doing so, you should have the missing 3rd option in the installer.

---

### Post by monguin61 on 2008-07-12
Thanks for your help, Skones. I did end up redoing the partition from within windows, and that seems to have solved the problem. For future reference, I think one of my issues was that my second partition was an "extended" partition, when I reformatted it as a second "primary", the Ubuntu installer was able to use it. 

However, it still made me resize the partition, so I used 99.9% of the second partition that I had made specifically for Ubuntu, and now I guess theres another little partition that I don't want. 

Either way, I got the install working and I'm very happy with it so far.

Does anyone have a recommendation for a good media player?

---

### Post by SkonesMickLoud on 2008-07-12
> **monguin61 said:**
> Does anyone have a recommendation for a good media player?

There's "vlc" "audacious" "amarok" among others.

All of these can be installed by running:

```
sudo aptitude install <name of program>
```

Or by browsing Add/Remove Programs and/or Synaptic.

---

### Post by NGKEIB on 2008-07-12
VLC - it can play anything, music or video.  Is also very useful for streaming and stuff.  You can get it in the Add/Remove thing if you check all available applications.

---

