---
title: "Dual Boot Ubuntu + Windows"
date: 2012-11-03
forum: Installation &amp; Upgrades
---

### Post by singlebinary on 2012-11-03
I used the windows installed "wubi" to create a dual boot on my Windows 7 Machine. Before running the installer, I created a partition of 300 GB for Ubuntu.  In the wubi, I chose 5 GB as installation choice and ran the whole process. 

I find that my entire home directory is not inside of 5GB (/dev/loop0) rather than the 300 GB I allotted. Below is my filesystem. How do I move my home directory to /sda5? 

```

Filesystem      Size  Used Avail Use% Mounted on
/dev/loop0      4.5G  4.1G  456M  91% /
udev            3.9G  4.0K  3.9G   1% /dev
tmpfs           1.6G  948K  1.6G   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            3.9G  1.2M  3.9G   1% /run/shm
/dev/sda5       293G  5.0G  288G   2% /host




```

---

### Post by oldfred on 2012-11-03
That would be a partitioned install not a wubi install. Wubi is just a file inside the NTFS Windows partition and uses the Windows boot loader.

If you want a partitioned install you want a full install. Is sda5 just wubi and not in the " c: drive "?

Ubuntu will not install to NTFS formatted partitions unless using wubi.
[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)
[https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi)

Wubi is fine for an extended test over just using liveCD, but is not intended for long term installs and is not true dual boot.
From the developer of wubi:
[http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/](http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/)
Agostino: Wubi actually wasn’t designed to do long-term installations. The main aim was really to let people try out Ubuntu with confidence. Normally, users that start with Wubi tend to upgrade to a full installation to a dedicated partition at the next release cycle.

[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)
[http://howtoubuntu.org/how-to-install-ubuntu-12-04-precise-pangolin/](http://howtoubuntu.org/how-to-install-ubuntu-12-04-precise-pangolin/)
Install 12.04- side by side auto install
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

---

### Post by singlebinary on 2012-11-03
Thanks oldfred for a quick reply. I used Wubi because I thought it was the best solution to dual boot Windows with Ubuntu. When I ran Wubi, I could only choose between 5 and 30 GB, which I thought was rather small. Hence, I created a partition, called it UBUNTU, named it as "i:drive" and left it as NTFS. I reran Wubi installer. However, this time, I chose "i:drive" from list of drives and installed Ubuntu. 

It seems to have created this weird /dev/loop0/ where my /home folder is situated. I am able to access the directory I made, /dev/sda5 or /host. I would like to change my /home to be in /dev/sda5 or /host. How do I do this? 

Goal: All I want to know is what is the best option so that my home folder is in the 300 GB partition and not in 4.5 GB. If you suggest reinstall, please let me know how to remove wubi and make a fresh install without reinstalling Windows. 

Thanks,

---

### Post by oldfred on 2012-11-03
If sda5 is a separate partition with no other data to save and you have not used wubi enough to save anything from it, it would be easiest just to start over.

The graphical install examples posted above show how to install. You can do default which is just root & swap or add additional partitions in your extended for / (root), swap & /home. If dual booting with Windows I often suggest a separate NTFS shared data partition also.

For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home if allocating over 30GB.:

Ubuntu partitions - smaller root only where hard drive space is limited.
If total space less than about 30GB just use / not separate /home or standard install.
1. 10-25 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext4(or ext3)
3. 2 GB Mountpoint swap logical

Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)

---

### Post by RealGomer on 2012-11-04
Let's see if I understand this. If I want to install Ubuntu (12.10) to dual boot with Windows 7 (Home Premium 64) it's best to do a direct install from Ubuntu and NOT use the wubi package. (This might explain why my PC will only boot once or twice before I have to repair the Windows boot manager and then loosing the dual boot option.) 
I was under the impression from the downloads page that using wubi allowed one to use the windows installer & windows boot manager.\ instead of GRUB. Is that correct?
I tell the wubi to install Ubuntu onto a logical drive - partition H: with 40GB.

---

### Post by oldfred on 2012-11-04
Wubi is fine if you just want to try Ubuntu, do not want to add partitions and want to boot with the Windows boot loader. But it is restricted to 30GB in a NTFS partition and is just a file in that NTFS partition so it is not a true dual boot. Any issues with the NTFS partition may also corrupt the wubi file.

---

