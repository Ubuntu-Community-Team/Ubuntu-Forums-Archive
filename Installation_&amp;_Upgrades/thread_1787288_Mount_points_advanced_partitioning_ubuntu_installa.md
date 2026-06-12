---
title: "Mount points advanced partitioning ubuntu installation"
date: 2011-06-20
forum: Installation &amp; Upgrades
---

### Post by makuab on 2011-06-20
I am having trouble with the advanced partitioning, I dont know what any of the mount points are for. I have a 64GB SSD which I want to use only for the boot files, and I have a 640GB which I want to place everything else on, as to preserve the life of the SSD. How should I configure my mount points/partitions in the ubuntu 11.04 installer?

---

### Post by makuab on 2011-06-20
come on, waiting at the install screen.

EDIT should I just put /boot on the SSD and /swap and /root and /home on the HDD?

---

### Post by oldfred on 2011-06-20
We are not an instant response site. We are just volunteers who want to help others or "pay it forward". the forum request you only "bump" once per 24 hours.

There have been several threads recently with suggestions on SSDs. Have you tried search? Those threads did have some specific recommendations, but I did not save links.

Herman on advantages/disadvantages of separate system partitions post#3
[http://ubuntuforums.org/showthread.php?t=1410392](http://ubuntuforums.org/showthread.php?t=1410392)

Arch suggests if not using windows and have BIOS use gpt and leave the / (root) only 25% used. You have to decide exactly how you want to configure partitions.
[https://wiki.archlinux.org/index.php/Solid_State_Drives](https://wiki.archlinux.org/index.php/Solid_State_Drives)
[https://wiki.ubuntu.com/MagicFab/SSDchecklist](https://wiki.ubuntu.com/MagicFab/SSDchecklist)
Not required with newer kernels
[http://disktrim.sourceforge.net/](http://disktrim.sourceforge.net/)


It does not have to be encrypted BIOS based system:
Standard full install with screenshots to flash or SSD:
Ubuntu Encrypted Flash Memory  Installation
[http://members.iinet.net/~herman546/p19.html]("http://members.iinet.net/%7Eherman546/p19.html")
More discussion Dec 2010, more SSD info
[http://ubuntuforums.org/showthread.php?t=1643591](http://ubuntuforums.org/showthread.php?t=1643591)
[http://ubuntuforums.org/showthread.php?t=1404664](http://ubuntuforums.org/showthread.php?t=1404664)

Use ext2 or ext4 without journal:
tune2fs -O ^has_journal /dev/sda1
No swap or set swapiness
After installing, change the fstab so that everything gets mounted with noatime.
change to noop i/o scheduler

You want journal to speed up system recovery if you have to do repairs or run fsck. But if partition is small then it does not take long to fsck anyway and without journal writing is reduced.
SSD&#8217;s, Journaling, and noatime/relatime 
[http://thunk.org/tytso/blog/2009/03/01/ssds-journaling-and-noatimerelatime/](http://thunk.org/tytso/blog/2009/03/01/ssds-journaling-and-noatimerelatime/)

Large HDD/SSD Linux 2.6.38 File-System Comparison: EXT3, EXT4, Btrfs, XFS, JFS, ReiserFS, NILFS2
[http://www.phoronix.com/scan.php?page=article&item=linux_2638_large&num=1](http://www.phoronix.com/scan.php?page=article&item=linux_2638_large&num=1)
Tuning Solid State Drives in Linuxcheckbox
[http://cptl.org/wp/index.php/2010/03/30/tuning-solid-state-drives-in-linux/](http://cptl.org/wp/index.php/2010/03/30/tuning-solid-state-drives-in-linux/)

---

### Post by makuab on 2011-06-20
> **oldfred said:**
> We are not an instant response site. We are just volunteers who want to help others or "pay it forward". the forum request you only "bump" once per 24 hours.

There have been several threads recently with suggestions on SSDs. Have you tried search? Those threads did have some specific recommendations, but I did not save links.

Herman on advantages/disadvantages of separate system partitions post#3
[http://ubuntuforums.org/showthread.php?t=1410392](http://ubuntuforums.org/showthread.php?t=1410392)

Arch suggests if not using windows and have BIOS use gpt and leave the / (root) only 25% used. You have to decide exactly how you want to configure partitions.
[https://wiki.archlinux.org/index.php/Solid_State_Drives](https://wiki.archlinux.org/index.php/Solid_State_Drives)
[https://wiki.ubuntu.com/MagicFab/SSDchecklist](https://wiki.ubuntu.com/MagicFab/SSDchecklist)
Not required with newer kernels
[http://disktrim.sourceforge.net/](http://disktrim.sourceforge.net/)


It does not have to be encrypted BIOS based system:
Standard full install with screenshots to flash or SSD:
Ubuntu Encrypted Flash Memory  Installation
[http://members.iinet.net/~herman546/p19.html]("http://members.iinet.net/%7Eherman546/p19.html")
More discussion Dec 2010, more SSD info
[http://ubuntuforums.org/showthread.php?t=1643591](http://ubuntuforums.org/showthread.php?t=1643591)
[http://ubuntuforums.org/showthread.php?t=1404664](http://ubuntuforums.org/showthread.php?t=1404664)

Use ext2 or ext4 without journal:
tune2fs -O ^has_journal /dev/sda1
No swap or set swapiness
After installing, change the fstab so that everything gets mounted with noatime.
change to noop i/o scheduler

You want journal to speed up system recovery if you have to do repairs or run fsck. But if partition is small then it does not take long to fsck anyway and without journal writing is reduced.
SSD&#8217;s, Journaling, and noatime/relatime 
[http://thunk.org/tytso/blog/2009/03/01/ssds-journaling-and-noatimerelatime/](http://thunk.org/tytso/blog/2009/03/01/ssds-journaling-and-noatimerelatime/)

Large HDD/SSD Linux 2.6.38 File-System Comparison: EXT3, EXT4, Btrfs, XFS, JFS, ReiserFS, NILFS2
[http://www.phoronix.com/scan.php?page=article&item=linux_2638_large&num=1](http://www.phoronix.com/scan.php?page=article&item=linux_2638_large&num=1)
Tuning Solid State Drives in Linuxcheckbox
[http://cptl.org/wp/index.php/2010/03/30/tuning-solid-state-drives-in-linux/](http://cptl.org/wp/index.php/2010/03/30/tuning-solid-state-drives-in-linux/)

Im trying to decrypt what you said.. but honestly, what? Im just trying to figure out what the mount points do, and how to install ubuntu so that I can preserve my SSD.

---

### Post by oldfred on 2011-06-21
See my first link to Herman on system partitions, it also applies to SSDs. But with SSDs, you may want to move some partitions to a rotating drive. Some have suggested that.

My SSD install (hopefully soon) will follow my own logic of each drive must have all boot files on it and be independently bootable. Or if another drive fails then this drive will still boot. Having partitions on different drives may speed things up slightly or reduce wear. Some have calculated wear on SSDs and it is longer than most rotating drives anyway. I do have data on various drives, but each drive will boot even if it cannot mount all the data partitions.

If you have lots of RAM some suggest putting /tmp in RAM, but I want to write DVDs of 4.2GB and only have 4GB of RAM, so I will not do that.

The links and some other threads explain a lot more than one post can cover.

---

### Post by makuab on 2011-06-21
> **oldfred said:**
> See my first link to Herman on system partitions, it also applies to SSDs. But with SSDs, you may want to move some partitions to a rotating drive. Some have suggested that.

My SSD install (hopefully soon) will follow my own logic of each drive must have all boot files on it and be independently bootable. Or if another drive fails then this drive will still boot. Having partitions on different drives may speed things up slightly or reduce wear. Some have calculated wear on SSDs and it is longer than most rotating drives anyway. I do have data on various drives, but each drive will boot even if it cannot mount all the data partitions.

If you have lots of RAM some suggest putting /tmp in RAM, but I want to write DVDs of 4.2GB and only have 4GB of RAM, so I will not do that.

The links and some other threads explain a lot more than one post can cover.

So how exactly can i put boot on the SSD and everything else on one partition on the HDD, if you can only have 1 mount point per partition?

---

### Post by oldfred on 2011-06-21
You do not want just /boot on the SSD. You want all or most of the operating system. I do not recommend separate /boot for desktops even with SSD.

[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)
[http://en.wikipedia.org/wiki/Disk_partitioning](http://en.wikipedia.org/wiki/Disk_partitioning)

GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)
Partitioning basics with some info on /data, older but still good bodhi.zazen
[http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition](http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition)

---

