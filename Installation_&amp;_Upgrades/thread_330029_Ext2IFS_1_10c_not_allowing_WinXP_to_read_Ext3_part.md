---
title: "Ext2IFS_1_10c not allowing WinXP to read Ext3 partition"
date: 2007-01-02
forum: Installation &amp; Upgrades
---

### Post by shamruse on 2007-01-02
New dual-boot system: ext3 or FAT32 for shared space?
Quote:
Originally Posted by aysiu View Post
I've had no problems at all with FS-Driver.
It's not a pain to install, and it works perfectly.

FAT32 is annoying because:

1. It gets extremely fragmented
2. It doesn't support user permissions in either environment
3. It can't handle file sizes larger than 4 GB

I would recommend Ext3 as the way to go.
I downloaded the Ext2IFS_1_10c file and I ran it in Windows XP. I chose a drive letter (U\ for my ext3 partition. Windows claims the drive is not formatted, so I can see it in my computer but I can't access any of the files on it.

My partitions are as follows:
8GB NTFS (Windows XP Installed)
60GB Ext3 (Ubuntu Home)
8GB Ext3 (Ubuntu 6.10 Installed, root)
1GB SWAP (Swap partition for Ubuntu)

I had planned to share the 60GB partition with both XP and Ubuntu so I can keep files on it, such as documents, downloaded media etc. that I can use in either OS. The sad part is I can't access this 60GB in winXP even with the Ext2IFS program.

I did not mount the 8GB or the 1GB partitions when i ran the program, I didn't want Windows XP getting its grubby little hands on it.

Does anyone know how I can have my dream configuration where both XP and Ubuntu can share a nice Ext3 partition but XP and Ubuntu won't touch the space reserved for their operating systems?

I got this idea from Aysiu, I have been following Aysiu step by step as I change to linux (loved your article as to why any given "this year" is not the year for linux because I agree 100%). But my transition has hit its first bump, and I would really appreciate linux newbie advice for handling this. I am very experienced with Windows, I program in C++, PHP, and AJAX. I have no problems with computers, it is just the learning curve here and my lack of time to sift through all the varying opinions. A trojan broke the camel's back and that is why I decided to dual boot with XP and Ubuntu, I wanted to be 100% ubuntu, but upon seeing the fuzzy text my eyes became to hurt and I had to retreat back to XP for reading text. An idiot proof guide to get Ubuntu text to look as sharp as XP would also be appreciated, I hate booting into XP to read this forum.

---

### Post by zeno86 on 2007-03-09
I hate to revive an old thread, but it may be helpful to others in the future.

In case you haven't got your answer, the Ext2/3 filesystem should be recognized in XP as you've done, but I have noticed that if Ubuntu isn't shut down/rebooted properly (e.g. a crash) then windows doesn't recognize the drive and will ask to format it. 

To remedy, you have to boot into linux and shutdown/restart properly and then it will be recognized correctly in XP.

---

