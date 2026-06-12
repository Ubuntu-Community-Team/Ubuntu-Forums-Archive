---
title: "create a partition and install windows 7"
date: 2011-03-12
forum: Installation &amp; Upgrades
---

### Post by paccamura on 2011-03-12
Hi,
I just started using ubuntu on my laptop... At the moment is the only operative system available on my machine... 
Unfortunately I need to install Windows 7 too because I need it for my job.
can somebody please help me creating a partition and installing windows?
will I be able to access the files stored on my pc from both the operative systems?

I recently replace the hard drive and at the beginning I created a bit of mess because I first installed windows 7, than ubuntu on a partition (splitting the hard-drive about 50%) and then, as I was having problems with windows I decided to just keep ubunto, so I reinstalled it on the hole hard drive (I guess)

is there any way to see if a partition already exist?
at the moment I see:
215,007 items, totalling 4.5 GB
(some contents unreadable)
+
269.8 GB

The exact size of the hard drive is around 320 GB, so it looks like something is missing...

thanks in advance for your help

---

### Post by YesWeCan on 2011-03-12
Hi there.
Would you post the output of 'sudo fdisk -l' so we can see your existing partitions?

---

### Post by kansasnoob on 2011-03-12
While booted into Ubuntu post the output of these two commands:

```
sudo parted -l
```

```
df -H
```

BTW that's a lower case L at the end of the first and deliberately a CAP H at the end of the last.

Also what exactly is the Win7 installation disc? Branded or unbranded? I ask because some Win7 re-installation media actually restores a machine to it's "factory state" :(

In a number of ways it actually is much easier to begin with Windows and then install Ubuntu second. Either way you'd need to back up anything important before proceeding.

---

### Post by paccamura on 2011-03-12
> **YesWeCan said:**
> Hi there.
Would you post the output of 'sudo fdisk -l' so we can see your existing partitions?

root@mario-Precision-M2300:/home/mario# sudo fdisk -l

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000d6bc4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       38149   306425856   83  Linux
/dev/sda2           38149       38914     6142977    5  Extended
/dev/sda5           38149       38914     6142976   82  Linux swap / Solaris

thanks

---

### Post by paccamura on 2011-03-12
> **kansasnoob said:**
> While booted into Ubuntu post the output of these two commands:

```
sudo parted -l
``````
df -H
```BTW that's a lower case L at the end of the first and deliberately a CAP H at the end of the last.

Also what exactly is the Win7 installation disc? Branded or unbranded? I ask because some Win7 re-installation media actually restores a machine to it's "factory state" :(

In a number of ways it actually is much easier to begin with Windows and then install Ubuntu second. Either way you'd need to back up anything important before proceeding.

root@mario-Precision-M2300:/home/mario# df -H
Filesystem             Size   Used  Avail Use% Mounted on
/dev/sda1              309G   3.5G   290G   2% /
none                   1.1G   291k   1.1G   1% /dev
none                   1.1G   386k   1.1G   1% /dev/shm
none                   1.1G    91k   1.1G   1% /var/run
none                   1.1G      0   1.1G   0% /var/lock

---

### Post by oldfred on 2011-03-12
With only 3.5 GB used it looks like a basic install with possibly a few updates but not a lot.

If you have made changes you want to keep, backup all of /home. If you have installed a lot of applications, make a list (see below) and use that to reinstall all the apps easily. If you made any system changes/custom configurations for special hardware back those up. Do all this regardless of how you decide to change things. I will suggest one possibly and others may/should have different opinions. There is no one right answer.

from lovinglinux - use dpkg to list installed apps
[http://ubuntuforums.org/showpost.php?p=7157175&postcount=5](http://ubuntuforums.org/showpost.php?p=7157175&postcount=5)

My suggestion is to start over. Install windows first, create a shared partition, then install Ubuntu.

How much space do you want for windows?

One suggestion
40-50GB windows NTFS with boot flag
50GB windows data NTFS

Extended partition (and then inside it)
20GB Linux / (root)
2GB swap
rest of drive /home

If your windows is a full installer you can create all the partitions in advance with gparted and install windows. If your windows disk is a recovery disk it will overwrite the entire drive and from within windows you can shrink that partition to make room for everything else. Then use gparted to make the addition partitions. Use manual install in Ubuntu to choose the /, swap & /home partitions for the install.

GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)
[http://members.iinet.net.au/~herman546/p22.html](http://members.iinet.net.au/~herman546/p22.html)
[http://news.softpedia.com/news/Installing-Ubuntu-10-10-160966.shtml](http://news.softpedia.com/news/Installing-Ubuntu-10-10-160966.shtml)
Maverick partition by hand to use free space:
[http://sites.google.com/site/easylinuxtipsproject/partitioning](http://sites.google.com/site/easylinuxtipsproject/partitioning)
[http://www.linuxbsdos.com/2010/10/12/ubuntu-10-10-manual-disk-partitioning-guide/](http://www.linuxbsdos.com/2010/10/12/ubuntu-10-10-manual-disk-partitioning-guide/)
[http://www.dedoimedo.com/computers/ubuntu-maverick.html](http://www.dedoimedo.com/computers/ubuntu-maverick.html)

---

