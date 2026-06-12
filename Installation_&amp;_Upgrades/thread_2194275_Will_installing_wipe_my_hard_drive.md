---
title: "Will installing wipe my hard drive?"
date: 2013-12-17
forum: Installation &amp; Upgrades
---

### Post by dellaxrobia on 2013-12-17
So, I'm somewhat of a noob here, but I would assume installing Ubuntu wouldn't wipe my hard drive? I know that it wipes OS from a hard drive unless you set it up not to, but I have two physically set up hard drives, and I know that I'll be installing Ubuntu on the other one (Windows 7 is on this) but I have a ton of backed up Music, Movies, and games on there so I just wanted to be completely sure that it won't actually wipe it when installing? I'm installing 13.10 by the way if it helps/matters at all.

---

### Post by sudodus on 2013-12-17
Welcome to the Ubuntu Forums :-)

I'm glad use ask before you try. Because installing operating systems and editing partitions on hard disk drives, HDD, and other 'mass storage devices' or drives is ***risky***. Usually things are going the right way, but there are too many failures that result in loss of data.

So either install into a new HDD or ***backup your data to an external drive or to a cloud service before you go ahead***.

If you want to install Ubuntu, you need to create space for it. You have to shrink an existing partition, and create two new partitions, one for the root file system '/' and one for 'swapping'. Do that when you have booted your computer from a live CD/DVD/USB drive (with Ubuntu and the partitioning tool ***Gparted***.

You need at least 8 GB for the root partition, but I would recommend at least 20 GB. And you need at least the same size in GiBibytes as the RAM if you want to hibernate. Otherwise you can have less, maybe 1 Gibibyte even in a new computer with a lot of RAM.

---

### Post by ajgreeny on 2013-12-17
I assume your second hard disk is formatted as ntfs, which is fine for data if running Ubuntu, but not for the OS itself.

You will need to make another partition on the disk for the Ubuntu OS root partition; I would recommend 20GB as does sudodus, and format it as ext4, but you can leave the formatting until installation.

If you have all your data in the ntfs partition on this same disk as Ubuntu you could make soft links from the ntfs partition to folders in your ubuntu home, so that everything would show automatically as if it was actually in your home.  That requires that the ntfs partition is automounted at boot by editing /etc/fstab in ubuntu, and this could possibly be complicated slightly if you have similar data files spread across more than one partition and/or physical disk, so tell us more detail and we can give you more idea of what is possible.

---

