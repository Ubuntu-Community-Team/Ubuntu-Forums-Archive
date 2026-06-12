---
title: "Transfer old /home to new install - new hard drive"
date: 2010-10-27
forum: Installation &amp; Upgrades
---

### Post by jmszr on 2010-10-27
Hello all, 

I'm going to be adding a new hard drive, installing 10.04.1 onto it and then transferring /home from the 8.04.4 install on the original hard drive.

My first question is if the 10.04.1 install will recognize the existing hard drive and if I should reformat the 8.04 / partition first - leaving the old /home and swap temporarily? Will there be any conflicts with having 8.04 already installed? Another question I have is whether I need to do anything special with the /home during installation (I'm just concerned that I'll wind up with a /home within a /home)? Should I just disconnect the current hard drive temporarily? I am obviously ignorant about all this, so any direction would be welcome.

I have been reading a lot of documentation about transferring the old /home and have seen it being done with rsync, cp, and dd. I'm leaning towards rsync, but any recommendations?

I have already  saved /opt, /var/cache/apt/archives, “save markings as” in synaptic, Firefox profile, and a sources.list.backup and, of course, I'll back up /home. I feel as if I'm still missing something(s) though – I just don't know what. 

Thanks for any and all help.

---

### Post by oldfred on 2010-10-28
Are you going to keep using old drive? If so then you just use manual install and choose your current /home as the partition for /home and choose not to format. You have to use manual install and partition for the new drive first. If you want everything on the new drive you need to move /home to the new partition. 

Any new drive requires some partition planning. What do you want to do for the next few years (before next new drive). Have lots of data, photos, video etc, or perhaps try out other systems. Each decision may determine a better way to partition.  Will you upgrade in place or every 6 months do a new install.  If lots of data perhaps an additional /data partition. If additional installs of Ubuntu or others perhaps additonal system partitions of 20GB. Your decision.

If you want /home on new drive. You just need to create & move to new partition, then as part of install use the new parition.
To move /home uses rsync  
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)
Uses cp -ax
[http://www.ivankuznetsov.com/2008/04/moving-home-to-its-own-partition.html](http://www.ivankuznetsov.com/2008/04/moving-home-to-its-own-partition.html)
[http://ubuntuforums.org/showthread.php?t=46866](http://ubuntuforums.org/showthread.php?t=46866)
cp without -a and copying as sudo root takes ownership (not good)
Uses cpio
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)


[https://help.ubuntu.com/community/InstallingANewHardDrive](https://help.ubuntu.com/community/InstallingANewHardDrive)
Partitioning basics with some info on /data older but still relevant
[http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition]("http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition")
GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
[http://www.ibm.com/developerworks/linux/library/l-resizing-partitions-1/index.html](http://www.ibm.com/developerworks/linux/library/l-resizing-partitions-1/index.html)

---

### Post by jmszr on 2010-10-28
oldfred,

Thanks for your response.

It makes sense to partition the new hard drive and transfer the old /home to it and then install 10.04.

The old hard drive is a 3 year old 250 GB Maxtor and I think I'd rather put /home on the new 500GB WD Caviar Black. I'm going to keep the old one installed, but truthfully it's more space than I'll need - however, it will be perfect for bug testing the development releases and trying other distros.

Thanks again,
Jeff

---

