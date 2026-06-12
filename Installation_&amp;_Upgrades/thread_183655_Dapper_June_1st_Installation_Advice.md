---
title: "Dapper June 1st Installation Advice"
date: 2006-05-28
forum: Installation &amp; Upgrades
---

### Post by Dark Elitist on 2006-05-28
Hello! 8) 

I have helped several friends get setup with 5.10 over the last month or so. They enjoy using Ubuntu very much and have been quite impressed with it. Because of this, I have decided that once Dapper is complete and released, I will tripple boot it with Windows. Honestly, I would like to really get rid of Windows but due to my use of many Windows applications that are unsupported by Wine and have no Linux counterparts, I must keep it.

Anyway, here is my question. I have two 120 (111 formatted) gigabyte drives. My hardware is a Dell Dimension 8100, XP2 Bios (Latest), P4 1.7, 256 meg GeForce FX5700 AGP, SoundBlasterLive, onboard 3Com Nic, 768 megs of ram. I was wondering what you all think of this partition layout and the reasons behind it:

HD1:

61440 NTFS PRIMARY Windows 2000 Professional
- All software, excluding games, that is not native to Ubuntu.

30720 NTFS PRIMARY Windows XP Professional
- This installation will be heavily tweaked and receive no installation of any antivirus or other security software outside of the included firewall. Because of this, it will never go on the internet except for Microsoft Update. Only games that don't run native to Ubuntu will be installed in XP. XP will be purely a gaming OS; WarCraft III & Expansion, Guild Wars, etc.

128 EXT3 PRIMARY /boot
- Grub will be installed here instead of to the MBR. I heard that doing this makes it easy to reinstall any of the operating systems installed on the machine since all that needs to be done is reactivate the bootable flag on /boot to regain the boot loader.

21376 EXT3 LOGICAL /
- Ubuntu's Home! I want to use Ubuntu for everything I possibly can! Go go Automatix Team! :D

HD2:

4096 NTFS LOGICAL Windows 2000 Swap File
- I need a large swap file for Windows 2000 because I do lots of Photoshop and Dreamweaver work, all at the same time. Even with 768, I often find myself with two gigabyte swap file usage.

1536 NTFS LOGICAL Windows XP Swap File
- Just gaming. With no background software except the minimal running, this should be plenty, I think.

30720 FAT32 LOGICAL Windows / Linux Storage and Transfer Partition
- I want to be able to easily transfer files to and from my Ubuntu installation. I heard Linux reads and writes to FAT32 just peachy! This partition would also be where temporary junk was kept.

61440 NTFS LOGICAL Windows 2000 My Documents Folder
- I think everyone in the community knows the reasons behind putting this folder on a separate drive.

1536 SWAP LOGICAL SWAPFILE for Ubuntu
- I will be playing Unreal Tournament 2004, Doom 3, Quake 4, etc. in Linux so I never want there to be issues.

14336 EXT3 LOGICAL /home
- Same reason and putting My Documents on a separate drive.

Alright. Let the advice roll in! Thank all of you very much! :D

[COLOR="Red"]**UPDATE:**[/COLOR] I have taken everyone's advice into consideration. The above has been modified. How's it look now?

---

### Post by pelle.k on 2006-05-28
well what can i say... looks great to me :)

---

### Post by Dark Elitist on 2006-05-28
[QUOTE=pelle.k]well what can i say... looks great to me :)[/QUOTE]

Thanks! I spent a lot of time on it! :D

To accomplish the above, am I going to want to use the new graphical installer or the traditional text-based installer? I was going to use a Gparted Live CD to do everything. Is that wise or should I use the Windows CDs for the Windows partitions, etc.

---

### Post by christhemonkey on 2006-05-28
I would use the windows disc to partition and install windows first. (and then defrag, just to be on the safe side!)

Then use ubuntu live CD to partition the rest.


Actually come to think of it, does a windows disk contain sufficient partition tools?
You could always just install and then reduce the size of the windows partition(s).


Also, must say, i like this partitioning scheme!  And your setup in general!
Wish i had enough money to get myself one of these 
*dreams....*

---

### Post by hajk on 2006-05-28
Two comments:

1. No need to use a journalling FS on a 64MB /boot partition, I recommend the extremely conservative Ext2 FS.

2. You may want to avoid partitioning with GParted in the liveCD partitioner, there are many reports of problems doing it that way. My advice: do the partitioning manually while booted in some liveCD (Knoppix, or Dapper), using cfdisk for example. Also manually format the new partitions with the FS of choice (Ext3 is OK, I use JFS), using mkfs (and mkswap). Then, after rebooting in Dapper liveCD, start the installer, choose manual editing of partition table, but only assign the mount points to the new partitions AND check the reformat boxes. The installer will honour your choices, and all will be OK after that.

It worked for me...

---

### Post by Dark Elitist on 2006-05-28
[QUOTE=christhemonkey]I would use the windows disc to partition and install windows first. (and then defrag, just to be on the safe side!)

Then use ubuntu live CD to partition the rest.


Actually come to think of it, does a windows disk contain sufficient partition tools?
You could always just install and then reduce the size of the windows partition(s).


Also, must say, I like this partitioning scheme!  And your setup in general!
Wish I had enough money to get myself one of these 
*dreams....*[/QUOTE]

Thank you very much. I have been using computers since the days of Dos. I also still play X-COM, if that says anything. ;) 

I repair computers for a living. If it were not for my extensive knowledge of Windows and computers in general, I would be totally lost in nix I have to admit. There is a steep learning curve but stuff like partitioning is basically universal.

I found a long time ago that putting swap files on a second drive greatly improves performance because two drives are working instead of one. You should try it sometime if you get a chance... You will notice a big performance gain.

Both of my drives have 8 megs of cache, thankfully. They are Seagates. 8)

---

### Post by Dark Elitist on 2006-05-28
[QUOTE=hajk]Two comments:

1. No need to use a journalling FS on a 64MB /boot partition, I recommend the extremely conservative Ext2 FS.

2. You may want to avoid partitioning with GParted in the liveCD partitioner, there are many reports of problems doing it that way. My advice: do the partitioning manually while booted in some liveCD (Knoppix, or Dapper), using cfdisk for example. Also manually format the new partitions with the FS of choice (Ext3 is OK, I use JFS), using mkfs (and mkswap). Then, after rebooting in Dapper liveCD, start the installer, choose manual editing of partition table, but only assign the mount points to the new partitions AND check the reformat boxes. The installer will honour your choices, and all will be OK after that.

It worked for me...[/QUOTE]

Ah. I see. So shrink /boot to 64 megs and use EXT2 instead of EXT3. How exactly do I go about setting the bootable flag to /boot on and installing GRUB on /boot instead of the MBR? I know there are some commands and such to type, like /dev/hda# or something.

I have never used cfdisk, I don't think. Is it textbased? So using a Gparted Live CD from [here]("http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828") is a bad idea? What is the difference between EXT3 and JFS? Which does Ubuntu run best on? EXT3 is the default I guess, right? mkfs and mkswap are also terminal commands?

Thank you!

---

### Post by mlind on 2006-05-28
I would use separate EXT2/3 /boot partition and put rest of the stuff inside LVM.
I like LVM style very much now that I've learned how to use it. And maybe set
size of swap to size of my RAM.

---

### Post by christhemonkey on 2006-05-28
mkfs and mkswap are both terminal commands.

And yes i think that cfdisk is textbased.


I would think that using a Gparted live CD would be fine!

But Hajk said that people have had problems with using it.
My experience of using Gparted has been fine.

Although currently have completely messed up my ubuntubox... (though not through using Gparted!)
Cant wait for my Dapper CD so i can just reinstall over the top!


I would use EXT3 instead of JFS,
as ubuntu uses EXT3 journalising, so you have the benefits of both.

---

### Post by Dark Elitist on 2006-05-28
[QUOTE=mlind]I would use separate EXT2/3 /boot partition and put rest of the stuff inside LVM.
I like LVM style very much now that I've learned how to use it. And maybe set
size of swap to size of my RAM.[/QUOTE]

Thank you. How does LVM work exactly?

---

### Post by Dark Elitist on 2006-05-28
[QUOTE=christhemonkey]mkfs and mkswap are both terminal commands.

And yes i think that cfdisk is textbased.


I would think that using a Gparted live CD would be fine!

But Hajk said that people have had problems with using it.
My experience of using Gparted has been fine.

Although currently have completely messed up my ubuntubox... (though not through using Gparted!)
Cant wait for my Dapper CD so i can just reinstall over the top!


I would use EXT3 instead of JFS,
as ubuntu uses EXT3 journalising, so you have the benefits of both.[/QUOTE]

I have used Gparted when doing one of my friend's and it seemed fine.

Hey Hajk, can you maybe explain what kind of problems? I am trying to learn as much as possible.

Much thanks to the both of you!

---

### Post by hajk on 2006-05-28
[QUOTE=Dark Elitist]

Hey Hajk, can you maybe explain what kind of problems? I am trying to learn as much as possible.[/QUOTE]

GParted *as used in the liveCD installer* has given problems when the partition table is at all somewhat unusual (as yours is/will be), or if an alternative journalling FS is desired (like JFS or XFS). In my case, when I tried to do this in the Beta2 installer with GParted the installer would just quit. I was determined to use JFS, for a change, and found after much trial-and-error the way I mentioned in my earlier post. Others, with unusual partition tables, have reported their MBR hosed; this happened as early as Flight-7, is supposed to have been fixed since then, but I'm still seeing the odd report of trouble... you can find them as easily as I could in this Dapper forum and in the bug reports in Malone.

I don't think the problem is GParted per se, rather the way it is steered by the Installer which cannot deal properly with unusual requirements. Stands to reason, actually, as the number of combinations of possible partition tables and file systems must be huge. I'm not going to take any risk this way and am going to do it myself the old-fashioned way with terminal commands like cfdisk and mkfs...:cool:

---

### Post by Dark Elitist on 2006-05-28
[QUOTE=hajk]GParted *as used in the liveCD installer* has given problems when the partition table is at all somewhat unusual (as yours is/will be), or if an alternative journalling FS is desired (like JFS or XFS). In my case, when I tried to do this in the Beta2 installer with GParted the installer would just quit. I was determined to use JFS, for a change, and found after much trial-and-error the way I mentioned in my earlier post. Others, with unusual partition tables, have reported their MBR hosed; this happened as early as Flight-7, is supposed to have been fixed since then, but I'm still seeing the odd report of trouble... you can find them as easily as I could in this Dapper forum and in the bug reports in Malone.

I don't think the problem is GParted per se, rather the way it is steered by the Installer which cannot deal properly with unusual requirements. Stands to reason, actually, as the number of combinations of possible partition tables and file systems must be huge. I'm not going to take any risk this way and am going to do it myself the old-fashioned way with terminal commands like cfdisk and mkfs...:cool:[/QUOTE]

Thank you for the detailed response. Any good tutorials for the above mentioned commands? I want a rock solid installation! =)

---

### Post by hajk on 2006-05-28
Any tutorials for cfdisk, mkfs and mkswap? Well, the man pages are pretty good, but somewhat forbidding for novices. I guess a good guide could be found at Gentoo (I'm an ex-Gentoo user, liked it, but got tired of the daily compile grind and tool-chain hassles.) The Gentoo Install Handbook contains a pretty good guide on how to partition disks with cfdisk, what to do to format file systems on them, etc. Yes, that's what I recommend, even though I've now switched to Ubuntu.;)

---

### Post by gmc on 2006-05-28
> **Dark Elitist]Hello! 8) 

HD1:

61440 NTFS PRIMARY Windows 2000 Professional
- All software, excluding games, that is not native to Ubuntu.

20480 NTFS PRIMARY Windows XP Professional
- This installation will be heavily tweaked and receive no installation of any antivirus or other security software outside of the included firewall. Because of this, it will never go on the internet except for Microsoft Update. Only games that don't run native to Ubuntu will be installed in XP. XP will be purely a gaming OS said:**
> 256 EXT3 PRIMARY /boot
- Grub will be installed here instead of to the MBR. I heard that doing this makes it easy to reinstall any of the operating systems installed on the machine since all that needs to be done is reactivate the bootable flag on /boot to regain the boot loader.

31488 EXT3 LOGICAL /
- Ubuntu's Home! I want to use Ubuntu for everything I possibly can! Go go Automatix Team! :D
[/B]
HD2:

4096 NTFS LOGICAL Windows 2000 Swap File
- I need a large swap file for Windows 2000 because I do lots of Photoshop and Dreamweaver work, all at the same time. Even with 768, I often find myself with two gigabyte swap file usage.

768 NTFS LOGICAL Windows XP Swap File
- Just gaming. With no background software except the minimal running, this should be plenty, I think.

20480 FAT32 LOGICAL Windows / Linux Storage and Transfer Partition
- I want to be able to easily transfer files to and from my Ubuntu installation. I heard Linux reads and writes to FAT32 just peachy!

61440 NTFS LOGICAL Windows 2000 My Documents Folder
- I think everyone in the community knows the reasons behind putting this folder on a separate drive.

4096 SWAP LOGICAL SWAPFILE for Ubuntu
- I will be playing Unreal Tournament 2004, Doom 3, Quake 4, etc. in Linux so I never want there to be issues.

22784 EXT3 LOGICAL /home
- Same reason and putting My Documents on a separate drive.

Alright. Let the advice roll in! Thank all of you very much! :D

In my opinion, the BOLD entries are over kill and wasted space. You're /boot partition could be halved (128M) or even quartered (64M) unless you want to keep dozens of older kernels. Your / (root) partition is way too much. A full install of Ubuntu with just about every thing you could possibly install (including every window manager) would fit into 8G. Why not split that partition into 2, one for / (root) 12G and /var 8G and use the rest of the space else where.

Just a thought.

Gord

---

### Post by linuxbz on 2006-05-28
If you put a swap file on each disk, I THINK Ubuntu will use whichever one is best ... though there may be many factors involved, like IDE, SCSI, or SATA, etc.

---

### Post by Dark Elitist on 2006-05-28
[QUOTE=gmc]In my opinion, the BOLD entries are over kill and wasted space. You're /boot partition could be halved (128M) or even quartered (64M) unless you want to keep dozens of older kernels. Your / (root) partition is way too much. A full install of Ubuntu with just about every thing you could possibly install (including every window manager) would fit into 8G. Why not split that partition into 2, one for / (root) 12G and /var 8G and use the rest of the space else where.

Just a thought.

Gord[/QUOTE]

What is /var? 

Also, I will be installing Quake 1, Quake 2, Quake 3, Quake 4, Ultimate Doom, Doom 2, Final Doom, Doom 3, Doom 3: RoE, ET, ETF, RTCW, Unreal Tournament GOTY, Unreal Tournament 2003, Unreal Tournament 2004, and a few other things. I don't think that will fit in 8 gigs...

---

### Post by Dark Elitist on 2006-05-28
[QUOTE=hajk]Any tutorials for cfdisk, mkfs and mkswap? Well, the man pages are pretty good, but somewhat forbidding for novices. I guess a good guide could be found at Gentoo (I'm an ex-Gentoo user, liked it, but got tired of the daily compile grind and tool-chain hassles.) The Gentoo Install Handbook contains a pretty good guide on how to partition disks with cfdisk, what to do to format file systems on them, etc. Yes, that's what I recommend, even though I've now switched to Ubuntu.;)[/QUOTE]

Nice. Thank you.

I wonder how much longer it will be until Ubuntu combined with Wine will be able to replace Windows entirely for all tasks. In the time it takes Microsoft to release one operating system, Ubuntu is releasing quite a lot more with many improvements in each.

I can't help but wonder, however... Fedora comes with a firewall. Why doesn't Ubuntu? Is Firestarter the best option?

Also, is it a good idea to install Clam AV?

---

### Post by andb on 2006-05-31
You'd do well to set it up with LVM, basically it lets you take the partitions ad then inside create blocks that you can add to or remove from logical partitions. In effect it lets you change partition sizes dynamicaly. 

Swap file heaven! Its not too much work to share swap space. Havent done it myself, but I remeber seeing a howto to put swap into a file on a FAT partition, and then both win and linux can share the same partition, same file.  Since swap data isn't persistant, it doesn't mater what the os finds there, itll just write over it.

Transfering - Theres a great free driver to access ext2/3 drives for windows, reads but doesnt support journaling, so it accesses ext3 drives as though they were ext2. Youll find it here:
[http://www.fs-driver.org/download.html](http://www.fs-driver.org/download.html)

Worth noting though, Windows wont be able to see into the LVM drives. May be possible, Ive never looked into it. So, maybe leave that transfer as ext3 and use it for temporary storage (like your ipod backup) delete to transfer and restore the previous data after the transfer. 

I personally have a really small root, and a bigger /usr partition. My whole install, by the way is far less than 5 gig, and Ive got a bunch of programs I tested and forgot (didnt bother ;) to remove. Using LVM will let you later change sizes so you wont be wasteful. 4 gig swap for ubuntu will probably let you run about 250 programs simultaniously, by the way ;) Take a bit of time to look at the file structure to understand what goes in /boot, root, /usr, /tmp, /var. Also it'll help to understand what happens if they fill, and why they are often in seperate partitions also.

oh, and note that you'll be able to read your mydocs folder just fine. Write support is a bit shakey, so I just wouldnt do it.

Hope this helps a bit...

---

### Post by andb on 2006-05-31
Firewall support is built into the kernel. Ubuntu takes the option of not running any unneccessary servers, so there is nothing for the outside world to talk to, so why ned a firewall? I cant agree with it 100%, but yes, it is secure. Plus, most people are behind a firewall/router these days. Firestarter is really good and easy way to configure the kernel firewall. It does have some limitations, but for a normal desktop machine you'll probably never find them ;) There are other scripts which do more, but I quite like firestarter.

Why use an AV program? Just to make sure you dont pass on a virus. Even if you download one, it wont have an effect on a linux machine. I don't run one as I share very few attachments.

Wine? Well, it works most of the time (sometimes). Better just to move to a linux program with simmilar functionality, if possible. Games? I think you'll want to hang on to windows then. Until games are written to support Linux and the graphic drivers are written as well as they are in windows, gaming will just be better on MS. I have Ubuntu as a computer, Xbox for games. Works fine :)

---

### Post by andb on 2006-05-31
Cant get my thoughts together in one post! For more information like about directory structure, making filesystems, system setup and so on, Id really recommend [http://learnlinux.tsf.org.za/](http://learnlinux.tsf.org.za/)  . The linux courses have really good, usable docs. That the site is from the Shuttleworth Foundation doesnt hurt either ;) I think its the SysAdmin course that'll tell you the most about implementation, but the Fundementals will explain how everything is laid out. In fact, these courses are probably the best I've run accross for ease of understanding. I wonder if people in the Ubuntu community know about them...

---

### Post by socialSavant on 2006-06-01
[QUOTE=Dark Elitist]What is /var? 

Also, I will be installing Quake 1, Quake 2, Quake 3, Quake 4, Ultimate Doom, Doom 2, Final Doom, Doom 3, Doom 3: RoE, ET, ETF, RTCW, Unreal Tournament GOTY, Unreal Tournament 2003, Unreal Tournament 2004, and a few other things. I don't think that will fit in 8 gigs...[/QUOTE]
Whoa, do you like FPS's? Just a guess :mrgreen: 

I would like to mention that you don't necessarily need two (2) seperate partitions for Windows Swap files. You will only ever be booted into one at a time and they both can use the same partition w/o any conflict. This too may increase the amount of space you can use for frag'n oponents...

--socialSavant

---

