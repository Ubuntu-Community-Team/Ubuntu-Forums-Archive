---
title: "Help required with partitions on Ubuntu 14.04"
date: 2016-01-28
forum: Installation &amp; Upgrades
---

### Post by Ranger48 on 2016-01-28
Hi everyone,

I had a look at some of the threads dealing with partioning, and there are many, but I cannot find anything that deals with my specific problem.

I'm running Xubuntu 14.04 on an HP laptop with a 750GB hard disc. Now I want to install Distro Astro as a dual boot, but the partition shown in the DA installer doesn't make sense and I'm reluctant to try to resize a partition during installation. So, I had a look with Gparted, and it would seem that the entire hard disc is used. There are also partitions such as ubuntu--vg-root which I am not familiar with (please see attached screenshot gparted.png).

I then used the System Monitor to look at the file systems and that tells me that only 17% of the hard disc is used (see attached screenshot).

So, I am thouroughly confused, and have no idea of how to proceed. All I want to do, is resize the existing partition to about 400GB so that I can create a new partition on the 300GB part and install Distro Astro on it. Which one do I resize?

Any help would be much appreciated.

Thanks in advance.

---

### Post by Bucky Ball on 2016-01-28
Let's stick to the Gparted results. Can't help with Astro. Nothing to do with Ubuntu and who knows why that's showing what it is.

Simple answer: LVM equals an encrypted partition (or RAID?) as far as I know. It is not a matter of simply shrinking. Did you encrypt this partition when installing? 

I know nothing about resizing LVM partitions but [here are some clues for your research]("https://duckduckgo.com/?q=resize%20lvm%20partition%20ubuntu"). Hopefully someone who does know about this can join in soon. Good luck.

---

### Post by Ranger48 on 2016-01-29
Thanks Bucky. The link helped up to a point, but then I got stuck.

---

### Post by Bucky Ball on 2016-01-29
Best to explain what you got stuck on. I probably won't be able to help but it will help others who may. ;)

---

### Post by oldfred on 2016-01-29
I do not know LVM. But it is Logical Volumes that take up the entire physical partition. So from gparted the entire physical partition is used. You have to use LVM tools.

Some links:
 Advantages/Disadvantages LVM Post #9
[http://ubuntuforums.org/showthread.php?t=1586328&p=9917145#post9917145](http://ubuntuforums.org/showthread.php?t=1586328&p=9917145#post9917145)
[https://wiki.ubuntu.com/Lvm](https://wiki.ubuntu.com/Lvm)
[https://help.ubuntu.com/community/UbuntuDesktopLVM](https://help.ubuntu.com/community/UbuntuDesktopLVM)
      
 How to: Mount & Resize an Encrypted Partition (LUKS) also mount
[http://ubuntuforums.org/showthread.php?p=4530641](http://ubuntuforums.org/showthread.php?p=4530641)

---

