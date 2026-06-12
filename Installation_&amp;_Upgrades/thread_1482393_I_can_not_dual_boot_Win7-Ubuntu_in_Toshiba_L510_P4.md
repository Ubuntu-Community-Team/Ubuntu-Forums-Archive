---
title: "I can not dual boot Win7-Ubuntu in Toshiba L510 P406"
date: 2010-05-13
forum: Installation &amp; Upgrades
---

### Post by metaphongtov on 2010-05-13
I have win7 intalled first and when I installed Ubuntu 10.4, I could not be given an option to choose partition manually but entire disk option only. My disk have 4 partitions, one of them is for Ubuntu. I don't want to erase Win7 existing first so how can I do?

---

### Post by recluce on 2010-05-13
I am surprised that you don't get the option to use one of the available partitions. In that case, you should try the "alternate install" CD, which is available for download from  [www.ubuntu.com](www.ubuntu.com).

---

### Post by oldfred on 2010-05-13
If you have used all four then you have none left to install. If you have created a linux root partition and swap partition then you can install using the manual install and choose which partitions to use and what format. It actually finds swap and auto formats that without any additional help.

Linux can be installed to logical partitions in an extended if your one partition is available to make two.

[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)
GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)

[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)

Install karmic Screens shown with advanced button
[http://news.softpedia.com/news/Installing-Ubuntu-9-10-126370.shtml](http://news.softpedia.com/news/Installing-Ubuntu-9-10-126370.shtml)
[http://members.iinet.net/~herman546/p28/032_install-now.png](http://members.iinet.net/~herman546/p28/032_install-now.png)

---

### Post by metaphongtov on 2010-05-14
Before I used Toshiba Satellite A205, I could choose partition manually even I didn't reserve one blank partition for Ubuntu. I think maybe cos of SATA disk problem related. I've just tried alternative install of Ubuntu installer for Windows but I'm given the same result. Any ideas?

---

### Post by recluce on 2010-05-14
> **metaphongtov said:**
> Before I used Toshiba Satellite A205, I could choose partition manually even I didn't reserve one blank partition for Ubuntu. I think maybe cos of SATA disk problem related. I've just tried alternative install of Ubuntu installer for Windows but I'm given the same result. Any ideas?

I am not sure what you are trying to do here. I was not talking about "WUBI" (and I would not know anything about it). There are TWO versions of the Ubuntu install CDs: the "Live CD", which will allow you both to run a live Ubuntu system and the alternate install CD, which will NOT allow you to run a live system, but has many more options to actually install Ubuntu.

---

### Post by darkod on 2010-05-14
When you say you don't get the option for manual partitioning, you mean you don't get the option 'Specify partitions manually (advanced)' at all?
I haven't heard of that so far, that option should always be present even if your limit of 4 partitions is reached.
If you expect just a question which partition to use, you won't get that.
The screenshot attached is from 9.10 but 10.04 is similar. You don't have that option?

---

### Post by metaphongtov on 2010-05-14
Here is the detail about my computer: 

[IMG]http://i47.photobucket.com/albums/f163/metaphongtov/1-1.png[/IMG]

[IMG]http://i47.photobucket.com/albums/f163/metaphongtov/2-1.png[/IMG]

[IMG]http://i47.photobucket.com/albums/f163/metaphongtov/3-1.png[/IMG]

I can see all the partitions in disk utility but can not see them in the installer.

---

### Post by recluce on 2010-05-14
Again: have you tried to install from the alternate install CD?

Since you seem to ignore any suggestions in that direction, I am now out of here. Good luck.

---

### Post by metaphongtov on 2010-05-14
> **recluce said:**
> Again: have you tried to install from the alternate install CD?

Since you seem to ignore any suggestions in that direction, I am now out of here. Good luck.
  
I don't get what you mean. I already try Wubi. Could u show me where the alternate install cd is? I already download ubuntu-10.04-desktop-i386.iso but I dun have blank cd to write yet. Before I used to install ubuntu 8.04 by cd installer though the same fail.

---

### Post by darkod on 2010-05-14
[http://releases.ubuntu.com/lucid/](http://releases.ubuntu.com/lucid/)

Scroll down where the images are and get the one with 'alternate' in the file name, not 'desktop'.

But I can't guarantee it will work. I'm confused by the screenshots you posted. I don't know what to do right now.

---

### Post by metaphongtov on 2010-05-14
> **darkod said:**
> [http://releases.ubuntu.com/lucid/](http://releases.ubuntu.com/lucid/)

Scroll down where the images are and get the one with 'alternate' in the file name, not 'desktop'.

But I can't guarantee it will work. I'm confused by the screenshots you posted. I don't know what to do right now.

As you can see in the Disk utility, I have 5 partitions: xp, ubuntu, Unknown(linux swap), Win7 and Data. I start installing till the step "Prepare disk space", I can choose "Specify partitions manually" but next step I can not see any partition appear, only one partition 250059 Mb (mean my whole hard disk). Now I am downloading the alternate CD to try, I hope it works!

---

### Post by metaphongtov on 2010-05-21
I have tried the alternative disk installer but still fail to choose partition manually. I can not see the partition that i preserve to install Ubuntu but only entire hard disk option is given :(

[IMG]http://i47.photobucket.com/albums/f163/metaphongtov/IMAG0164.jpg[/IMG]
[IMG]http://i47.photobucket.com/albums/f163/metaphongtov/IMAG0165.jpg[/IMG]

---

### Post by metaphongtov on 2010-05-25
Anyone use the same laptop?

---

### Post by Mark Phelps on 2010-05-25
Apologize if you've already tried this, but the GParted LiveCD tends to have newer versions of GParted than do the distro images.

Suggest you download and burn the GParted LiveCD ISO (which you can get from distrowatch.com) and see if that recognizes the partitions better.  If it does, shrink the NTFS data partition to make room for Ubuntu, and use the same LiveCD to create the Ext4 partitions inside the Extended partition.

With those partitions in place, the alternate CD should then be able to see them and, if so, you can install using them.

---

### Post by darkod on 2010-05-25
Can you boot ubuntu cd in live mode and post the result of:

sudo fdisk -l (small L)

Recently in another thread when the disk was recognized as big empty space it was a problem that a partition was reported as going outside the disk. The fdisk command will show us the cylinders count.

---

