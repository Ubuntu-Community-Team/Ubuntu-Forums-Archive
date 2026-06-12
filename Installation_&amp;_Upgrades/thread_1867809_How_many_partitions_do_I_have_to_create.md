---
title: "How many partitions do I have to create ?"
date: 2011-10-23
forum: Installation &amp; Upgrades
---

### Post by evroniano on 2011-10-23
At the moment I'm writing from a LIVE CD of 11.10 Ubuntu and I want to install it and completely remove my windows xp.
At the moment I have 2 partitions,
NTFS with Windows XP installed (15 GB)
NTFS with documents and folders and programs  450GB

1) how many partitions do I have to create ? I remember from my last linux installation (mandriva in 2004 I think) that I have to create a lot of linux partitions.
2) Please can you recommend a size for each partition ? When I first installed windows I chose only 5 GB for the file system partition and the result was that the partition after 2 days was full, I had to resize the partition and this took me 15 hours xD
3) Unfortunately I cannot backup my 450 GB partition because I haven't got a free external hard drive and so I cannot create a partition, is it safe to access NTFS files from Linux ? can this make the system slower ?
4) I have a very old pc (2005) 1GB RAM, 2 GHZ AMD64, 256 MB NVIDIA 6200 TURBOCACHE, and ubuntu on live cd isn't so fast, will the system be faster after a proper installation ?

---

### Post by khelben1979 on 2011-10-23
1. I recommend to use several partitions, just as you have done before:  [http://en.wikipedia.org/wiki/Disk_partitioning#Benefits_of_multiple_partitions]("http://en.wikipedia.org/wiki/Disk_partitioning#Benefits_of_multiple_partitions") 
(make a note that the /root partition haveto be at least 2.4 GB in size in accordance with the Ubuntu 11.10 installer)

2. It's really hard to say, it all comes down to how you intend to use your Linux system. If it's a Linux system where many people log in, then you should make sure to have a very large /home partitions for all users, and if you intend to install a lot of applications it's a good idea to have a big /usr partition. So it all depends, and I think it's important to understand what each partition does and how it works.

3. I would not recommend having an NTFS filesystem for Linux if it's intended for the Linux operating system, if it's for storage only, there is no problems. Use EXT3 or EXT4 would be my recommendation.

4. Very old? Mine is from 2002. ;) I've tested Ubuntu 11.10 on it, works just fine! YES, it will run faster because the LiveCD slows down the Ubuntu system quite a lot.

---

### Post by nothingspecial on 2011-10-23
> **evroniano said:**
> 
3) Unfortunately I cannot backup my 450 GB partition because I haven't got a free external hard drive and so I cannot create a partition, is it safe to access NTFS files from Linux ? can this make the system slower ?


I wouldn't go about partitioning drives and installing operating systems unless I had a back up of all my data......

.....or I didn't care if I lost it.

It will probably be fine, but there is always a risk.

Get an external drive before you do this.

---

### Post by tommcd on 2011-10-23
To evroniano,

If you only want Ubuntu as the only OS on your computer, you should ideally create 3 partitions:

1. A root partition of about 20GB. This is where the Ubuntu OS will live.

2. A swap partition. If you would like to use suspend to memory, then swap should at least be equal to, (or up to 2X of) the amount of memory that you have on the computer. If you do not plan to suspend to memory, then just create a swap partition of 1GB and forget about it. Swap is analogous to *virtual memory* in Windows XP.

3. The rest of the hard drive will be your home partition. Home is where your user specific settings and all of your personal data will live.
All of your "*documents and folders*" on your current 450GB NTFS partition can be stored on the new Ubuntu home partition.

NOTE: You will need to backup all the data that you want do not want to loose on your current 450GB NTFS partition. Then copy this data to your new home partition on Ubuntu after you install Ubuntu.

The root and swap partitions can be *primary* partitions. The home partition should be *logical*. This will give you the flexibility to create additional logical partitions in the future if you ever wish to do so. I would use the *ext4* file system for all of my linux partitions.

This is how I would partition my hard drive if Ubuntu were the only OS on my computer. If I were getting rid of Windows and just using Ubuntu then I would get rid of all the NTFS partitions and just copy the data back to the new linux partitions after Ubuntu is installed.
A root, swap, and home partition is the simplest and most ideal partitioning scheme. 
There are many different opinions on this matter though. In the time I spent typing this, several people already posted there own ideas before I could finish posting this!!
See this tutorial on creating a sparate home partition when you install ubuntu: [http://www.psychocats.net/ubuntu/installseparatehome](http://www.psychocats.net/ubuntu/installseparatehome)
Write back if you need more help.

And welcome to the Ubuntu forums!

---

### Post by kurt18947 on 2011-10-23
You only REALLY need to create one partition.  You need swap with only 1 GB. system RAM but you can create a  swap FILE rather than a swap PARTITION.  You only NEED a swap partition if you want to hibernate (suspend to disk).  To suspend to disk you need a swap partition somewhat larger than your physical RAM.  Swap files used to be slower than swap partitions.  That seems to no longer be the case.  The advantage to a swap file is that it doesn't use up one of the 4  primary partitions that a hard drive can have.  

The way people get around the 4 partition limit is to create an extended partition with volumes in it.  I don't know if a swap partition can be in an extended partition.   I've only done swap files and haven't had a memory problem.  Of course, I don't use hibernate (suspend to disk), I either suspend to RAM or shut down.  I've had zero issues with Ubuntu reading and writing NTFS partitions.

---

### Post by presence1960 on 2011-10-23
> **evroniano said:**
> At the moment I'm writing from a LIVE CD of 11.10 Ubuntu and I want to install it and completely remove my windows xp.
At the moment I have 2 partitions,
NTFS with Windows XP installed (15 GB)
NTFS with documents and folders and programs  450GB

1) how many partitions do I have to create ? I remember from my last linux installation (mandriva in 2004 I think) that I have to create a lot of linux partitions.
2) Please can you recommend a size for each partition ? When I first installed windows I chose only 5 GB for the file system partition and the result was that the partition after 2 days was full, I had to resize the partition and this took me 15 hours xD
3) Unfortunately I cannot backup my 450 GB partition because I haven't got a free external hard drive and so I cannot create a partition, is it safe to access NTFS files from Linux ? can this make the system slower ?
4) I have a very old pc (2005) 1GB RAM, 2 GHZ AMD64, 256 MB NVIDIA 6200 TURBOCACHE, and ubuntu on live cd isn't so fast, will the system be faster after a proper installation ?

1 & 2. I would use gparted either from Ubuntu Live CD or a gparted Live CD to create 2 partitions. A 13 GB ext 4 partition for ubuntu & a 2 GB linux-swap partition. Once you complete that you will choose a manual install from Ubuntu Live CD.

3. Your NTFS data partition is perfectly fine. However I would recommend a back up of those files as nothing can be guaranteed when doing partitioning & OS installation. 99% of time all goes well, however do you want to leave it to chance about the other 1%? If your files are important I would find a way to back them up first.

4. Your machine should be fine with Ubuntu, I have installed it on machines like that many times.

**_Again I reiterate it is strongly suggested you make a backup of your files  or you run the risk of losing them should an unlikely error occur. Remember **** happens-nothing is guaranteed!_**

I assumed you wanted to get rid of windows and use that partition to create linux partitions. Sorry if I asumed wrong. If you want to dual boot with windows you will have to shrink the 450 GB partition to create space for ubuntu. You can then use that unallocated space to create an extended partition with 2 logical partitions for ubuntu (ext 4 & linux-swap). You would then use the manual install option from Ubuntu Live CD

---

### Post by westie457 on 2011-10-23
> **evroniano said:**
> At the moment I'm writing from a LIVE CD of 11.10 Ubuntu and I want to install it and completely remove my windows xp.
At the moment I have 2 partitions,
NTFS with Windows XP installed (15 GB)
NTFS with documents and folders and programs  450GB

1) how many partitions do I have to create ? I remember from my last linux installation (mandriva in 2004 I think) that I have to create a lot of linux partitions.
2) Please can you recommend a size for each partition ? When I first installed windows I chose only 5 GB for the file system partition and the result was that the partition after 2 days was full, I had to resize the partition and this took me 15 hours xD
3) Unfortunately I cannot backup my 450 GB partition because I haven't got a free external hard drive and so I cannot create a partition, is it safe to access NTFS files from Linux ? can this make the system slower ?
4) I have a very old pc (2005) 1GB RAM, 2 GHZ AMD64, 256 MB NVIDIA 6200 TURBOCACHE, and ubuntu on live cd isn't so fast, will the system be faster after a proper installation ?

Hello welcome to the Forum.

First thing take a look at this link 
[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition) for some information on partitioning.

Personal advice from me. Leave the XP partition where it is and at the size it is, any smaller and Windows will not run properly.

DO EVERYTHING FROM A LIVECD/USB
Boot the CD and start Gparted.
Select the 450GB partition and resize it down to about 300GB (if you have enough empty space in it), I will explain why later. Click on Okay and then Apply. Wait for this to finish.

In the new unallocated partition Select NEW and create a Logical-extended partition. Click as above.

Now the fun begins. 
In the extended partition (here you can create as many as you want. However for now we are going to create three Partitions. They are going to be ROOT, HOME and SWAP when you do your install.

Remember we are in the extended partition. 
Create the SWAP partition make it about 2GiB and place it at the right as far as it will go. Next is your ROOT, this need to be about15GB which is plenty of room, this goes to the Left edge.
The remaining space can be created as your HOME partition, using all of the space or making it about 20GB leaving a lot of free space for extra distros to be installed if you wish.
The ROOT and HOME partitions can be left blank or formatted to EXT3 or 4.

Creating the partitions this way will save a lot of time in the future if you want extra flavours of LINUX/UBUNTU and minimizes the risk of data loss when it all goes wrong.


When you have finished the partitioning work close Gparted and click on the INSTALL icon on the Desktop. The installer will start. When it gets to 'Where do you want to install' **choose the 'Something Else' option** this will bring up a window to allow you to use your pre-created partitions.

Hope this helps without being confusing.


+++++++++++++++++++++++++++++++++++++++++++++++++++++

WOW. Ninja'd by 5 replies. 
+1 to those who suggested **_BACKUP your files first._**

---

### Post by Morbius1 on 2011-10-23
1. As few as possible. Swap + Root ( i.e., / ) is all you need. Anything more is silly. If you had more room I would suggest a separate data partition. I don't think much of a separate home partition. 

3. Nothing wrong with accessing an ntfs partition.

What you can do given the constraints of not having the ability to back up the the NTFS data partition is to permanently mount the partition and then "bind" parts of it to your home directory.

For example, say you have the 450 GB partition mounted at /media/NTFS. You can create say a Videos folder on that partition and then bind it to the Videos folder in your home directory:
```
sudo mount --bind /media/NTFS/Videos /home/morbius/Videos
```That's a temporary mount but the point is you now have the ability to save things to the much larger partition instead of the relatively small partition where your home folder is located.

You can also set this up to happen at boot: [http://ubuntuforums.org/showthread.php?p=10899012#post10899012](http://ubuntuforums.org/showthread.php?p=10899012#post10899012)

---

### Post by evroniano on 2012-01-16
ah ok, ty guys, really helpful, at the moment I have got some problems with my windows xp, maybe the file system is corrupted, so the pc doesn't boot and I'm considering installing Ubuntu and deleting everything except the data.
I'm about to partition the drive, about the /root and the /home, what file extension do you recommend ? someone said it's better to leave it blank, or maybe ext3 or ext4 ?
is it OK to do root and swap partitions primary and home logical ?

---

### Post by mastablasta on 2012-01-16
> **evroniano said:**
> ah ok, ty guys, really helpful, at the moment I have got some problems with my windows xp, maybe the file system is corrupted, so the pc doesn't boot and I'm considering installing Ubuntu and deleting everything except the data.

Then delete just the windows partition.
> 
I'm about to partition the drive, about the /root and the /home, what file extension do you recommend ? someone said it's better to leave it blank, or maybe ext3 or ext4 ?
ext3 is not file extension it is file format. windows uses NTFS. i would say ext4 is OK.
 
if you just delete the winXP partition and then install ubuntu onto it, this root, swap, home will be done automaticly in that part of the disk. well home will be a directory not a partition (and will realyl act like My documents on winXP). but you plan to put your data probably on the NTFS partition you already have. which you can do.
 
note: if you wish to convert the NTFS into ext4 you will have to reformat it (which erases the data).
 
> 
is it OK to do root and swap partitions primary and home logical ?
 
yes. but like i said why complicate? root and swap will be done automaticly by installer. Home is ment for users data and settings, but you plan to use the existing NTFS partition for data as i underdstand.

---

