---
title: "How to configure MBR to point to GRUB"
date: 2011-08-11
forum: Installation &amp; Upgrades
---

### Post by pckrfan75 on 2011-08-11
So I am interested in running Ubuntu side-by-side with my windows 7. It appears that the Ubuntu 11.04 installer does most of the work for me as partitioning according to: [https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot) but the only thing it says that I would be having to do myself is changing the code on my MBR to point to the GRUB2. I am not afraid of command prompts, but would like some hand holding as I don't wwant to guess and check when dealing with MBR. 

Also, a few miscellaneous questions:

1. Is there any way to share documents between my Ubuntu partition and Windows partition? Or some way to make it so documents and non OS specific files are accessible by both OSs?

2. Is it recommended to let Ubuntu do the partitioning for me? Or is there something to be gained by partitioning myself?

As you can tell I am fairly new to the world of Linux and whatnot, so basic speech would be appreciated.

Thanks in advance!

---

### Post by dino99 on 2011-08-11
config grub2:
 sudo dpkg-reconfigure grub-pc
there check your hdd(s) (some kind of: /dev/sdx, where x is a->z)

sharing:
sudo apt-get install samba ntfsprogs ntfs-3g winbind

installing:
i prefer to partition myself and dont use the installer doing blindly things
[http://ubuntuforums.org/showpost.php?p=10161428&postcount=2](http://ubuntuforums.org/showpost.php?p=10161428&postcount=2)

---

### Post by pckrfan75 on 2011-08-11
> **dino99 said:**
> config grub2:
 sudo dpkg-reconfigure grub-pc
there check your hdd(s) (some kind of: /dev/sdx, where x is a->z)

sharing:
sudo apt-get install samba ntfsprogs ntfs-3g winbind

installing:
i prefer to partition myself and dont use the installer doing blindly things
[http://ubuntuforums.org/showpost.php?p=10161428&postcount=2](http://ubuntuforums.org/showpost.php?p=10161428&postcount=2)
 
Thank you! I think I get the gist of what you mean but just to clarify, all the sudo stuff is being typed into a Terminal command line, yes?

And the only other thing is with that partitioning scheme, you appear to be running a solely Ubuntu system, mine is being dual booted with windows.

---

### Post by pckrfan75 on 2011-08-11
> **Major_Bloodnok said:**
> With an Ubuntu 11.04 new install, the user ( you ) does NOT touch the MBR; 
GRUB will sort all of that out, for you.

Overall steps.
- Just update win7 to service pack 1, plus any other updates. 
- Backup your win7 personal file/s.
- IF win7 occupies the whole hard drive, you NEED TO create free partition WITHIN win7.
- Install ubuntu.
- When the ubuntu install ask you which partition to use, select the free partition you created in win7.

partitioning Ubuntu inside win7 doesn't make much sense to me. Why wouldn't I partition it after win7 and just mount my hdd to ubuntu and change program directories?

---

### Post by Hakunka-Matata on 2011-08-11
> **pckrfan75 said:**
> partitioning Ubuntu inside win7 doesn't make much sense to me. Why wouldn't I partition it after win7 and just mount my hdd to ubuntu and change program directories?

It is generally accepted that to make partition changes to WIndows partitions, it's safer to use Window's tools.
How is your hard drive partitioned now?

[LIST]
[*]post a graphic from windows disk manager or:
[*]post a graphic from Ubuntu's GParteded partition manager, how?
[*]boot your machine to a Ubuntu LiveCD/usb and use GParted under System>Administration>GParted
[/LIST]
It is likely that windows has used all four primary partitions (four primaries is the maximum allowed on MBR discs) on your hard drive, if that's the case, there is work to be done before you can create any new partitions.

---

### Post by pckrfan75 on 2011-08-11
> **Hakunka-Matata said:**
> It is generally accepted that to make partition changes to WIndows partitions, it's safer to use Window's tools.
How is your hard drive partitioned now?

[LIST]
[*]post a graphic from windows disk manager or:
[*]post a graphic from Ubuntu's GParteded partition manager, how?
[*]boot your machine to a Ubuntu LiveCD/usb and use GParted under System>Administration>GParted
[/LIST]
It is likely that windows has used all four primary partitions (four primaries is the maximum allowed on MBR discs) on your hard drive, if that's the case, there is work to be done before you can create any new partitions.

Windows is only using 3 of my primary partitions, so currently (in preperation for my Ubuntu install) I have partitioned my hard drive as follows:

1. DellUtility (Primary fat16) 100MB
2. Recovery (Primary ntfs) 14.65 GB
3. OS (Primary ntfs) 565 GB
4. Extended (ntfs) 15 GB

My theory behind my partitioning currently is to not touch 1 or 2 for obvious reasons, but I want to throw the Ubuntu OS into a 10 GB logical partition on the extended with 5 GB left for Swap purposes, and then mount my 565 GB primary partition where all of my music and files are stored into Ubuntu so I can change program directories to download and save to there. This way I have all of my files both on windows and Ubuntu. I just need to figure out how to tell Ubuntu I only want the OS installed into that 10 GB partition and not install the typical Os/home/swap partition configuration that seems to be default for Linux.

---

### Post by Hakunka-Matata on 2011-08-11
> **pckrfan75 said:**
> Windows is only using 3 of my primary partitions, so currently (in preperation for my Ubuntu install) I have partitioned my hard drive as follows:

1. DellUtility (Primary fat16) 100MB
2. Recovery (Primary ntfs) 14.65 GB
3. OS (Primary ntfs) 565 GB
4. Extended (ntfs) 15 GB

My theory behind my partitioning currently is to not touch 1 or 2 for obvious reasons, but I want to throw the Ubuntu OS into a 10 GB logical partition on the extended with 5 GB left for Swap purposes, and then mount my 565 GB primary partition where all of my music and files are stored into Ubuntu so I can change program directories to download and save to there. This way I have all of my files both on windows and Ubuntu. I just need to figure out how to tell Ubuntu I only want the OS installed into that 10 GB partition and not install the typical Os/home/swap partition configuration that seems to be default for Linux.

Generally your idea is sound I think.  15GB is small but enough for an Ubuntu / (root) and Swap partition.  Do you already have the disk partitioned as you state above?  I ask because # 4. Extended won't be a ntfs partition.  Can you attach a graphic of your current partitioning?
**EDIT:  **ummhh, I don't know about storing/installing Linux programs to partition #3, that might be a problem.  You can certainly store Data on partiton #3 while running Ubuntu however.  Seems to me you might be better off using windows tools to shrink partition #3, to free up a bit more space.  If you decide to do that, there is an important sequence of steps to take though.  Like first defrag the OS twice before shrinking it, and booting into windows once or twice after that before starting with the Ubuntu install.  Which version Windows do you have installed?

---

### Post by pckrfan75 on 2011-08-11
> **Hakunka-Matata said:**
> Generally your idea is sound I think.  15GB is small but enough for an Ubuntu / (root) and Swap partition.  Do you already have the disk partitioned as you state above?  I ask because # 4. Extended won't be a ntfs partition.  Can you attach a graphic of your current partitioning?
**EDIT:  **ummhh, I don't know about storing/installing Linux programs to partition #3, that might be a problem.  You can certainly store Data on partiton #3 while running Ubuntu however.  Seems to me you might be better off using windows tools to shrink partition #3, to free up a bit more space.  If you decide to do that, there is an important sequence of steps to take though.  Like first defrag the OS twice before shrinking it, and booting into windows once or twice after that before starting with the Ubuntu install.  Which version Windows do you have installed?

I am running Windows 7. And you're correct, I made a mistake when I typed ntfs as the extended, that was typed mildly absentmindedly.  Basically the reason I want to be storing data on partition 3 is because I still do plan on using windows. I don't want to have to download music for my windows and linux partition seperately. Maybe programs was a bit too far to attempt to go with this but for sure data. I plan on using both OS. So what you would suggest is defragging twice, shrinking the Windows partition down to allow more room for actual ubuntu programs, booting in windows twice, and then installing ubuntu in the extended?

---

### Post by Hakunka-Matata on 2011-08-11
let me find a post that details the safe (est) way to do it.  I've read it many times (in various versions) and should be able to find it quickly,

---

### Post by pckrfan75 on 2011-08-11
Sounds good! That or I was wondering what would happen if I delete my Dell Utility Partition (#1) and it seems that as long as I have a windows 7 install disk it is a fairly safe endeavor. So would Deleting that and making my partitioning scheme:

1. Windows OS
2. Windows Recovery
3. Ubunto OS
4. Shared Partition for data

Does that make more sense?

---

### Post by Hakunka-Matata on 2011-08-11
[http://www.thpc.info/how/shrink_partition_in_windows_7_vista.html](http://www.thpc.info/how/shrink_partition_in_windows_7_vista.html)

I would read that for sure, every time I find a new post, or link discussing Shrinking windows partitions, I see yet another potential problem point to consider.  It is quite interesting and is often a huge headache for people trying to setup a dual boot system after windows 7 has been running on their machine for a while already.  So there you go.

If your / (root) EXT4 partition for Ubuntu is 35-40GiB, that should last you for quite a while.  Suggesting anything over 20 GiB usually draws comments, but it all depends on how many extra packages, programs, apps you add.

---

### Post by Hakunka-Matata on 2011-08-11
> **pckrfan75 said:**
> Sounds good! That or I was wondering what would happen if I delete my Dell Utility Partition (#1) and it seems that as long as I have a windows 7 install disk it is a fairly safe endeavor. So would Deleting that and making my partitioning scheme:

1. Windows OS
2. Windows Recovery
3. Ubunto OS
4. Shared Partition for data

Does that make more sense?

There are infinite ways to do it, you're already setup OK I think.  Deleting, moving, resizing presents more opportunities for breaking something, but it can all be done.  Personally I think a separate ntfs data partition is a good idea, both windows and Ubuntu can access it, and if something does break there, it won't mess up either you windows or Ubuntu system partitions.

---

### Post by pckrfan75 on 2011-08-11
> **Hakunka-Matata said:**
> []("http://www.thpc.info/how/shrink_partition_in_windows_7_vista.html")

  It quite interesting and is often a huge headache for people trying to setup a dual boot system after windows 7 has been running on their machine for a while already.  So there you go.



No kidding... I wish I discovered Linux when I first got this computer. Would have saved me a bunch of work. Though since besides some music and pictures, there really is nothing essential on my computer, just some time and effort spent on installs of programs, considering doing a fresh start on this one... Ugh haha

---

### Post by Hakunka-Matata on 2011-08-11
> **pckrfan75 said:**
> No kidding... I wish I discovered Linux when I first got this computer. Would have saved me a bunch of work. Though since besides some music and pictures, there really is nothing essential on my computer, just some time and effort spent on installs of programs, considering doing a fresh start on this one... Ugh haha

In that case, you're in an excellent position.  Save your music and data off to some backup drive, or just make a ntfs partition with Ubuntu's GParted and save it off to that partition and don't MESS with it as you go about changing everything else around, playing.

You're sure you can reinstall Windows 7 with the discs you already have?  I understand Windows 7 allows you to create a set of discs to reinstall if you don't already have them?  XP SP3 is the latest version of windows I've ever had, so I can only go on what I read.

Have you tried or installed Ubuntu already?

---

### Post by YesWeCan on 2011-08-11
> **pckrfan75 said:**
> Windows is only using 3 of my primary partitions, so currently (in preperation for my Ubuntu install) I have partitioned my hard drive as follows:

1. DellUtility (Primary fat16) 100MB
2. Recovery (Primary ntfs) 14.65 GB
3. OS (Primary ntfs) 565 GB
4. Extended [s](ntfs)[/s] 15 GB

My theory behind my partitioning currently is to not touch 1 or 2 for obvious reasons, but I want to throw the Ubuntu OS into a 10 GB logical partition on the extended with 5 GB left for Swap purposes, and then mount my 565 GB primary partition where all of my music and files are stored into Ubuntu so I can change program directories to download and save to there. This way I have all of my files both on windows and Ubuntu. I just need to figure out how to tell Ubuntu I only want the OS installed into that 10 GB partition and not install the typical Os/home/swap partition configuration that seems to be default for Linux.
This looks very good. I think it is best to keep all your linux partitions in the extended container.
When you install Ubuntu select "manual" or "something else" and then you just highlight the free space under the extended partition and add partitions in it for root and swap. :)
Then check where it is installing the Grub boot loader, it will default to disk sda. If you only have one disk in your system then its probably sda so all is well. If you happen to have more than one disk then it is often better to install Grub to the other disk and boot off that disk instead. Because this leaves your Windows MBR code intact and allows you to still boot Windows directly if you need to.

---

### Post by YesWeCan on 2011-08-11
I just noticed that the 11.04 installer doesn't let you create an extended partition! So I'd suggest you boot off live CD and run System/Admin/GParted. You can use GParted to create an extended partition spanning your free 15GB of space and also to create your logical partitions inside it for root and swap. Then when you run the installer you just have to highlight the partitions and tell it to format them and set mount points.

A guide to GParted: [http://www.dedoimedo.com/computers/gparted.html#mozTocId309606](http://www.dedoimedo.com/computers/gparted.html#mozTocId309606)

---

