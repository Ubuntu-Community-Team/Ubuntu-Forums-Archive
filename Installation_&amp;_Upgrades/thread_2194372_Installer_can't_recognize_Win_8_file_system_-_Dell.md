---
title: "Installer can't recognize Win 8 file system - Dell XPS 15 (P31F) (2013 edition)"
date: 2013-12-18
forum: Installation &amp; Upgrades
---

### Post by eric_r2 on 2013-12-18
I have a new Dell XPS 15 P31F, but when I try to install Ubuntu on it, the installer is unable to properly detect the Windows 8 file system on the laptop. I want to install Ubuntu alongside Windows 8 preferably, though I'd also take installing it by itself and keeping my recovery partitions.

When I try to run the installer, the error I get is "No root filesystem detected. Please correct from the partitioning menu." I've opened up GParted to set up the file systems the correct way, but I'm not sure what to do.. Preferably I'd like to split the hard drive 50/50 between Ubuntu and Windows 8.

[IMG]http://imagebin.org/index.php?mode=image&id=282828[/IMG][IMG]http://imagebin.org/index.php?mode=image&id=282828[/IMG]

Screenshot of my options in GParted: [IMG]http://imagebin.org/index.php?mode=image&id=282828[/IMG]http://imagebin.org/index.php?mode=image&id=282828
The error I receive: [http://imagebin.org/index.php?mode=image&id=282829](http://imagebin.org/index.php?mode=image&id=282829)

---

### Post by fantab on 2013-12-18
Boot with Ubuntu DVD/USB and 'Try Ubuntu (Without Installing)', Open Terminal [Ctrl+Alt+T], run the following commands and post its output here:
```
sudo parted -l
sudo fdisk -l
```

The problem you describe is common when 'no space' has been left for Ubuntu as either 'unallocated space' or a Linux partition. The output from the above will tell us how your HDD is partitioned and we can advice you further based on the output.

---

### Post by oldfred on 2013-12-18
In addition to fantab's suggestion.

This is a UEFI system? And then is Windows 8 still hibernated? It uses a fast boot that is always hibernated unless you do specific things to turn off fast boot.

Also is it an Ultrabook with a small SSD?

 Ubuntu on the Precision M3800 or XPS15 Nov 2013
[http://en.community.dell.com/techcenter/b/techcenter/archive/2013/11/14/ubuntu-on-the-precision-m3800.aspx](http://en.community.dell.com/techcenter/b/techcenter/archive/2013/11/14/ubuntu-on-the-precision-m3800.aspx)

 Dell 14z & 17r with Intel SRT
[http://ubuntuforums.org/showthread.php?t=2038121](http://ubuntuforums.org/showthread.php?t=2038121)
Dell UltraBook - Instructions & Details in Post #15 & 16 Devine Shine
[http://ubuntuforums.org/showthread.php?t=2144853](http://ubuntuforums.org/showthread.php?t=2144853)

---

