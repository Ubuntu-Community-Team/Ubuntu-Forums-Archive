---
title: "SSD + HDD Setup"
date: 2012-12-27
forum: Installation &amp; Upgrades
---

### Post by BloodyDream on 2012-12-27
I have recently built a new computer, I have a 90GB SSD and a 2TB HDD. I have Ubuntu running on the SSD, but I've had a few problems (I encrypted the drive and now it can't be edited through Gparted, I didn't install the HDD before installing the OS (which is how it is supposed to be done with Windows but I've heard otherwise with Ubuntu)). SO I'm just going to re-install Ubuntu and start over since I barely have any files saved. I'd like the home folder to be on the HDD and the OS/Boot to be on the SSD. I've recently heard that putting the /home on the SSD too is actually better, but I don't have the space to hold all of the files (plus I heard that it can lower SSD life, I don't know the truth of that though)which is where I came across "symbolic links". What are these, how do they work, and how do I make them? I'm not using Windows, so all of the space on the SSD is for Ubuntu. However, I will be downloading/installing a lot of games, so I need those to be stored on the HDD since I don't have much room. Also, should I install the HDD before or after the OS? I'd like step-by-step instructions just so that I'm not confused, because I like to know what I'm doing and why rather than just doing it haha. I just want a pretty simple setup, that works.
Thanks

---

### Post by oldfred on 2012-12-27
With SSD & HDD, I also like to keep /home on the SSD but link all the folders in /home like Documents, Video, Music etc in a partition or two on hard drive. My /home is 2GB with about 3/4 of that .wine for Picasa.

Do not know about the new games & how large they may be. Generally applications are in / (root).

If only installing Ubuntu, never Windows you may want to consider gpt partitioning. Then you do not have any issues with primary, extended and logical partitions. They all are the same, but you only can have 128. :)
But if booting with BIOS you need a 1MB unformated bios_grub flagged partition for grub to install correctly. If UEFI you need the efi partition as FAT32 as the first partition. If drive might be ever moved to a UEFI system it is best to leave room or add the efi partition when first setting up drive as it is difficult to add partition at front of drive later.

I have no issue leaving drives plugged in an installing, but you do have to use Something Else or manual install and choose to install grub2's boot loader to the MBR of the same drive as your Ubuntu install. Many suggest unplugging drive, but some do not want to open case.

       For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home if allocating over 30GB.:
If gpt(not MBR) partitioning include these two first - all partitions with gpt are primary
    250 MB efi FAT32  (for UEFI boot or future use for UEFI)
    1 MB bios_grub  no format (for BIOS boot)
Ubuntu partitions - smaller root only where hard drive space is limited.
If total space less than about 30GB just use / not separate /home or standard install.
1. 10-25 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext4(or ext3)
3. 2 GB Mountpoint swap logical

   Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)
[http://ubuntuforums.org/showthread.php?t=2021534](http://ubuntuforums.org/showthread.php?t=2021534)

    
       [http://ubuntuforums.org/showthread.php?t=1981478](http://ubuntuforums.org/showthread.php?t=1981478)
[https://wiki.archlinux.org/index.php/Solid_State_Drives](https://wiki.archlinux.org/index.php/Solid_State_Drives)
    
       [https://wiki.archlinux.org/index.php/UEFI](https://wiki.archlinux.org/index.php/UEFI)
[https://wiki.archlinux.org/index.php/GPT](https://wiki.archlinux.org/index.php/GPT)
    
If installing with UEFI.
       You will need to use the 64 bit version of 12.10 and from the UEFI menu boot the flash drive in UEFI mode. That way it will install in UEFI mode.
Systems need quick boot or fast boot turned off in UEFI settings.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
[https://wiki.archlinux.org/index.php/UEFI](https://wiki.archlinux.org/index.php/UEFI)
[https://help.ubuntu.com/community/UEFIBooting](https://help.ubuntu.com/community/UEFIBooting)

    
       Splitting home directory discussion and details:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata](http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata)
Link is on move home but see post by bodhi.zazen on data partition #6
[http://ubuntuforums.org/showthread.php?t=325048](http://ubuntuforums.org/showthread.php?t=325048)

---

### Post by BloodyDream on 2012-12-27
What is linking and how do you do it? I've never even heard of it. Games are huge, 10-20GB sometimes. I know that most applications are, but is there a way to move them into /home or something? I have a ton of RAM and don't hibernate, computer is too loud plus boot is fast enough. I may leave a little for swap. How do I do all of this partitioning though?

---

### Post by oldfred on 2012-12-27
I always partition in advance with gparted, but I have some idea of the sizes of partitions I want. Auto install just installs / (root) and swap and auto chooses sizes.

Worth reviewing even if you use the partitioning during manual install. It works essentially the same way.
       GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)


I know nothing about games in Linux nor how large they may be. Most programs in Linux are a lot smaller than Windows. Some applications may install in other locations, but most applications have to be installed to system partitions. Not sure if games are the same or not.


Look in this sub-forum for some of the comments.
[http://ubuntuforums.org/forumdisplay.php?f=93](http://ubuntuforums.org/forumdisplay.php?f=93)

---

### Post by BloodyDream on 2012-12-27
How do you partition the drive in advance? I would rather do that, so that I don't have to resize swap and everything afterwards.

---

### Post by oldfred on 2012-12-27
See post #2 for suggestions on sizes.

Use gparted from Ubuntu liveCD, or download gparted or parted magic ISO and create liveCDs. You have to use liveCD to change partitions if you already have an install as all partitions must be unmounted.

       [http://partedmagic.com/](http://partedmagic.com/)
[http://gparted.sourceforge.net/faq.php](http://gparted.sourceforge.net/faq.php)

GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

---

### Post by BloodyDream on 2012-12-27
I know how to do that, but you said in advance. I thought that you meant that you could partition it before installing or something.

---

### Post by oldfred on 2012-12-27
That is what I do. But in the Ubuntu installer you still use Something else, but do not have to create partitions, just choose a partition, what format, and its use.

I have lots of partitions on one drive and have actually installed to the wrong one. So now I have to printout or write down a list before reinstalling to that drive. I have a variety of test installs on that drive all in 25GB partitions. I label them when I create them,  so I know which is which, but the installer does not show the labels.

---

### Post by BloodyDream on 2012-12-27
If I were to reinstall how would I partition it first? Clear the SSD and run a live CD (USB) and use Gparted? I'd like to just use the format like you posted, since you seem pretty knowledgeable. I'll make a list of them.

---

### Post by BloodyDream on 2012-12-27
I think I have the SSD formatted well now, I followed those partitions using the "other" option or whatever during installation. I've written down a guide as well, I'll probably post it around. And of course, credit you for the majority of it haha. Now I just need to fix my HDD.

---

