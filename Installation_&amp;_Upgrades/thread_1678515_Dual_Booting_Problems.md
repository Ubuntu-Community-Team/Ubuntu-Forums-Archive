---
title: "Dual Booting Problems"
date: 2011-01-30
forum: Installation &amp; Upgrades
---

### Post by ioioi210 on 2011-01-30
[INDENT][/INDENT]Hi, I have Ubuntu 10.10 on my laptop currently and my mom would like to have it on hers as well.  However, she does not want to get rid of Windows 7, or use Wubi (for some reason). So, my only choice is to dual boot it.

While I was installing it onto my laptop there was an option to choose the partitioning.  There wasn't an option to do this on my her laptop though because you can only have 4 partitions on a hard drive apparently. The partitions are: 

NAME (TYPE)

[LIST=1]
[*]System (NTFS)
[*]C: (NTFS)
[*]Recovery (NTFS)
[*]HP TOOLS (FAT32)
[/LIST]

Is there anyway to backup a partition (Like Recovery) and make it bootable from a flash drive/CD?  Or is there any other work around from this?

Thanks in advance!

---

### Post by Rubi1200 on 2011-01-30
Hi and welcome to the forums :-)

Some prerequisites:

1. backup all important data

2. create a repair/recovery CD: [http://www.sevenforums.com/tutorials/2083-system-repair-disc-create.html](http://www.sevenforums.com/tutorials/2083-system-repair-disc-create.html)

3. defragment the drives

4. if you want to install Ubuntu 10.10 beware that the installer can, and will, destroy Windows if you choose the install alongside option:
[http://ubuntuforums.org/showthread.php?t=1622388](http://ubuntuforums.org/showthread.php?t=1622388)

5. you can *probably* remove the recovery partition and HP tools partition

6. create space in Windows for Ubuntu using the Disk Management tool to shrink the Windows partition

7. decide in advance how much space you want to devote to Ubuntu and make a plan on paper before proceeding

8. use Google, the search function here on the forum, and ask as many questions as you want before starting

If you do all this, then the install and subsequent experience should be great.

I suggest you also listen to other opinions and ideas as to how to approach this, but this is more or less how I would go about it.

---

### Post by ioioi210 on 2011-01-30
Thanks Rubi1200!

I'll go through those steps during this next to make sure everything goes smoothing. In the meantime if anyone has any other advice I'll be happy to look into it :)

---

