---
title: "Dual boot installation hits windows"
date: 2008-10-05
forum: Installation &amp; Upgrades
---

### Post by GreenFuze on 2008-10-05
Hey everybody, I saw the same question in the archives, but there were no real answer over there, so I'm reopening the question.

I had a windows partition that I installed over it ubuntu.
After the installation, when I boot windows, it looks for that partition, causing the startup to be REALLY SLOW (a few minutes....!).
This is very frustrating! especially that I have to do some of my work on windows, and I boot many times.

The only solution I can think of (that is NOT TESTED - it is just a thought!), is to delete the Ubuntu partition in windows, causing windows to know there is no partition over there, so it won't look for it on start-up.
this way when one can installs windows on that partition, while windows won't try to check that partition, and causing start-up to be slow.
The only problem in this (might-work) solution, is that I HAVE to delete my ubuntu partition, which is not such a very good idea...

Does anyone have a better idea ???


Thanks!!! :-)

---

### Post by lemming465 on 2008-10-11
I'm a little confused by your problem description.  If I understand you correctly, you had C: and D: windows partitions, installed ubuntu onto D:, and now windows is slow on boot.

If that describes your situation, what may be confusing windows is the
disagreement between the partition type code and the filesystem.  Windows strongly prefers that those match.  If you post the Linux output from
```
sudo fdisk -l; cat /etc/fstab; df -m;
```
we might be able to offer more detailed advice.  

Typically NTFS/HPFS partitions are type 7; EXT2/EXT3 are type 83.  You change a partition type with the "t" command in Linux fdisk, but be careful with it, as fdisk is slightly dangerous.

---

### Post by Sef on 2008-10-12
>  I had a windows partition that I installed over it ubuntu.

So you used Wubi to install Ubuntu, or did you use a disk?

---

