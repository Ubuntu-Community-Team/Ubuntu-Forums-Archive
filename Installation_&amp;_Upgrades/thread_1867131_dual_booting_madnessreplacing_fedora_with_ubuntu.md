---
title: "dual booting madness/replacing fedora with ubuntu"
date: 2011-10-22
forum: Installation &amp; Upgrades
---

### Post by rx530ss on 2011-10-22
Hi, everyone. I'll get straight to the point.

**What I have**:
3 partitions. One with Fedora 15, one with windows xp, and another very large one that I use for my file system.

**What I want**:
3 partitions. One with ubuntu 11.10, one with windows xp, and another very large one that I use for my filesystem.

**My concerns**:
Basically what I want to do is erase my fedora partition and replace it with ubuntu. Right now I am using the fedora 15 boot-loader. So, my questions is, if I do that, will windows xp show up in the Ubuntu boot-loader? How do I do it without breaking my setup? If I do somehow ruin the xp boot-loader how do I fix it?

Thanks. :)

---

### Post by zvacet on 2011-10-22
Yes windows will show up in grub if you install Ubuntu.When you are talking about setup if you mean your partitions,then during install DO NOT FORMAT any other partition other then one on witch you will install Ubuntu.

---

### Post by drs305 on 2011-10-22
During installation, I'd select manual partitioning and point the installer to the correct partition. You will select the partition, then click on "mount point" and designate "/" and tick to format the partition.

The installation will install the Grub files within the Ubuntu partition, and write Grub information to the MBR, replacing whatever is there.

At some point during the installation you will be shown where Grub is going to be installed. Make sure it says "sda" and not a partition (such as "sda1" or "sda5").

During Grub installation, it should accomplish a search of your drive(s) and include any other OS's it finds. It generally does a good job of this.

When the system boots after the installation, you should see the Grub menu and the various OS's. If it doesn't, but boots into Ubuntu, it means that Ubuntu is properly installed but Grub failed to find the other OS's. In that case, open a terminal and run
```
sudo update-grub
```
This will accomplish another search and usually if Grub didn't find the OS's during installation it will on the second attempt.

---

### Post by rx530ss on 2011-10-23
Thanks to both of you, I will post the results when i'm done. :KS

---

