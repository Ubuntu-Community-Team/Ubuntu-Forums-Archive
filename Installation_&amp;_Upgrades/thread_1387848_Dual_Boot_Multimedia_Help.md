---
title: "Dual Boot Multimedia Help"
date: 2010-01-22
forum: Installation &amp; Upgrades
---

### Post by brian_utd7 on 2010-01-22
Hey guys, I have a question about dual booting windows 7 and ubuntu 9.10. What I want to be able to do is store my multimeda and open office files on a partition that can be read by both windows and ubuntu, I just don't know how to do this. What kind of partition should I make it? Should it be done in windows 7 or ubuntu?

---

### Post by ajgreeny on 2010-01-22
I have no idea what partitioning tools are available in win7, apart from the disk management utility which lets you shrink the windows partition.  Use that to do the shrinking, leaving you with an unallocated space.  If it's possible to do it in the disk management, make a second partition next to windows and format as ntfs.  Leave the final partition space unallocated.  If you can't make a new partition with the win7 disk management you will need to do it later in the ubuntu installation, though I am not sure if that allows you to format to ntfs.  If it does not, don't worry, you can format it to ntfs later after installing the ubuntu OS

Now boot to the live ubuntu CD, and using that, install ubuntu to the unallocated space at the end of the drive.  It should find the windows installation and add it to grub automatically.  The second ntfs partition,if you could make it earlier, will need to be mounted at boot time in ubuntu with an edited /etc/fstab file, or by using the various ntfs configuration utilities available in the repos.

Come back for more help if needed.

---

### Post by oldfred on 2010-01-22
[http://ubuntuforums.org/showthread.php?t=1387870](http://ubuntuforums.org/showthread.php?t=1387870)

You managed to dual post. You should only have one post per topic.

---

