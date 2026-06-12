---
title: "Confused by two wayys for installing Ubuntu"
date: 2010-08-24
forum: Installation &amp; Upgrades
---

### Post by garycheng12 on 2010-08-24
So I followed a video on Youtube that shows you how to install Ubuntu on an external hard drive by manually creating a swap partition, a root partition, and a home partition.

I was just wondering how this method differs from installing on a single partition -- both is bootable, but why may I need to do one over the other? 

In my scenario, I use only Windows on my desktop computer. I have Ubuntu installed on an external hard drive.


Also, I was wondering if I can create an image of the partition and then restore on a different partition in a different hard drive as long as the partition is at least the same size as the image. Before I can create this perfect image, though, I need to know how to prevent any drivers from automatically installing because this image could be used on different computers and I don't want different computers to carry unnecessary drivers that could complicate certain problems. How do I do this? Also, how can I uninstall drivers on Ubuntu?

Thanks, guys.

---

### Post by mörgæs on 2010-08-24
It does make sense to have a separate /home partition. When you install a new version of Ubuntu, you can delete all partitions except /home, so your files will not be lost during the installation.

---

### Post by ezsit on 2010-08-24
> Also, I was wondering if I can create an image of the partition and then restore on a different partition in a different hard drive as long as the partition is at least the same size as the image. Before I can create this perfect image, though, I need to know how to prevent any drivers from automatically installing because this image could be used on different computers and I don't want different computers to carry unnecessary drivers that could complicate certain problems. How do I do this? Also, how can I uninstall drivers on Ubuntu?

You can create images of partitions, using clonezilla, partimage, fsarchiver, and probably some more. However, for what you want to do, partition imaging is not what you want. 

Look into remastersys ([www.remastersys.com](www.remastersys.com)). This tool will create a live CD/DVD image of your installed system and allow you to reinstall from that image. It is a wondeful tool. Read the instructions, it ain't hard.

PS - Drivers don't work the way you are thinking. Also, using remastersys should be done before you install any prorpietary video drivers.

---

### Post by garycheng12 on 2010-08-25
> **mörgæs said:**
> It does make sense to have a separate /home partition. When you install a new version of Ubuntu, you can delete all partitions except /home, so your files will not be lost during the installation.

I don't know how that answers my question O_o, thanks for trying though, lol.

---

### Post by oldfred on 2010-08-25
The standard auto install just creates the / (root) and swap partitions. I originally used that with the addition of a shared NTFS partition for sharing data between XP & Ubuntu. If you want more than the standard partitions and want more control over the sizes, then you want to manually partition and use manual install.

If you install to an external or any second drive you need to use the advanced button to make sure grub2 is installed to the correct drive.
[http://members.iinet.net/~herman546/p28/032_install-now.png]("http://members.iinet.net/%7Eherman546/p28/032_install-now.png")

GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)

Dual boot 2 drives, windows & Lucid 10.04
[http://members.iinet.net.au/~herman546/p24.html]("http://members.iinet.net.au/%7Eherman546/p24.html")

[https://help.ubuntu.com/community/InstallingANewHardDrive](https://help.ubuntu.com/community/InstallingANewHardDrive)
[https://help.ubuntu.com/community/HowtoPartition/OperatingSystemsAndPartitions](https://help.ubuntu.com/community/HowtoPartition/OperatingSystemsAndPartitions)

---

