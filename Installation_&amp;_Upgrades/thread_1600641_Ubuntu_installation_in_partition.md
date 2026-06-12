---
title: "Ubuntu installation in partition"
date: 2010-10-19
forum: Installation &amp; Upgrades
---

### Post by blackwidowxxx on 2010-10-19
hi everybody.I have 160 GB harddish which has five partitions c,d,e,f,g.
In drive c,windows xp is installed.Now can i install ubuntu in any one other drive without causing changes to other drives and to windows xp in c drive.
 
i am in need of a help for this!:)

---

### Post by oldfred on 2010-10-19
Yes you should be able to reformat one partition. Ubuntu will want two  partitions one for root and one for swap. But depending on the size of the space you want to use for Ubuntu you can convert one to two. But it is always a good idea to have fresh backups just in case something goes awry. 

The issue may be where on the drive the partition(s) are. Under MBR (msdos) partitions you can only have 4 primary partitions. One primary may be converted to and extended partition and hold many logical. So it would be best if you convert one of you data partitions that is already in the extended.

GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
[http://www.ibm.com/developerworks/linux/library/l-resizing-partitions-1/index.html](http://www.ibm.com/developerworks/linux/library/l-resizing-partitions-1/index.html)

Maverick screens look a little different than older installs.
[http://news.softpedia.com/news/Installing-Ubuntu-10-10-160966.shtml](http://news.softpedia.com/news/Installing-Ubuntu-10-10-160966.shtml)
Maverick partition by hand to use free space:
[http://sites.google.com/site/easylinuxtipsproject/partitioning](http://sites.google.com/site/easylinuxtipsproject/partitioning)
[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)
Full Disk install Lucid Graphical
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

I always suggest using gparted to set up partitions in advance as the automatic install does not give as much control. It will resize the largest partition or arbitrarily make space/sizes of partitions. If you manually partition you can also add a separate /home partition but do not have to if just starting to use Ubuntu. Separate /home makes new installs easily as you save your settings.

One of many suggests on sizes:
Install with creating partitions screen shots
[http://members.iinet.net.au/~herman546/p22.html](http://members.iinet.net.au/~herman546/p22.html)

1. 10-20 GB Mountpoint / primary beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext3(or ext4)
3. 2 GB Mountpoint swap logical (or size of RAM memory)

---

### Post by kansasnoob on 2010-10-19
> **blackwidowxxx said:**
> hi everybody.I have 160 GB harddish which has five partitions c,d,e,f,g.
In drive c,windows xp is installed.Now can i install ubuntu in any one other drive without causing changes to other drives and to windows xp in c drive.
 
i am in need of a help for this!:)

You must first of all know what's contained within what partition/disc. have you been able to run the Ubuntu Live CD?

If so it would be interesting to see the output of the Boot Info Script prior to making any suggestions:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

More info might be needed but that's a good starting point.

---

### Post by sikander3786 on 2010-10-19
I don't think it is something that much complicated. I'd however like to see the output of

```
sudo fdisk -l
```

in order to know better about your partition setup.

You can do all that partitioning stuff right from the Installer's partitioning page itself. gparted is a better choice but not necessary.

**Oldfred** has got some very useful tips and references. He is a master in this field but I think posting that much information might confuse a newbie :-)

**kansasnoob** opted for bootinfoscript but I think output from **fdisk -l** should be sufficient.

I would like to advise only after you post the output of above mentioned command. For time being, you can always delete a partition, split it into 2 and install Ubuntu. You never need a primary partition to boot Ubuntu as is the case with Windows. Logical partitions will do the job.

The only thing that Ubuntu will replace in your old setup is the MBR. It will install Grub, the Ubuntu bootloader and let you dual boot between Windows and Ubuntu. You can also select not to install it during the installer and then you can go with Windows base boot loader EasyBCD. Whatever you prefer.

---

