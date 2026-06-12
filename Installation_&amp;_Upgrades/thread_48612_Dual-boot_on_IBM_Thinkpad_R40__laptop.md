---
title: "Dual-boot on IBM Thinkpad R40  laptop?"
date: 2005-07-13
forum: Installation &amp; Upgrades
---

### Post by eeried on 2005-07-13
Hello,

I'm new to this forum and an advanced newbie in Linux, if I can put it this way.

I'd like to install ubuntu on an  IBM Thinkpad R40  laptop alongside WinXP. As this isn't my computer  I can't just erase Windoze...

The Ubuntu Live CD works like a charm on this laptop.

IBM has a hidden partition (which shows in Linux as hda2). 

What's bothering me however is that even after defragmenting the C: partition in Windows, a number of files can't be moved and the are stuck right at the end of the partition. I suppose they are special IBM files, but I don't know for certain.

Can Ubuntu manage to resize the hda1  ntfs partition in this condition. Won't it erase the end of the partition?

PS: the computer was sold without a WinXP Cd-rom (IBM has a restoration function somewhere), I don't have the IBM rescue password. So I can't afford to make mistakes.

Your help would be very much appreciated,

eeried

---

### Post by javiadip on 2005-07-13
I am running Ubuntu and Win xp pro on IBM Thinkpad R52 right now. You won't be able to install ubuntu without formatting the C:. I tried doing that too, it didnt work. You will have to find an Windows XP CD in able to install ubuntu. If you cant find the Win XP Pro CD, you can do is make an image of your windows using Symantec ghost, I am not sure if it will record the partition tables or not, coz if it does it might try to restore all the parititon tables how it was when u imaged it which will put you where u are right now. So you dont want ghost to record partiton tables too, look for an option or something.  

If you have an Win XP CD, boot it up from there, delete all parititons, and make a FAT32 paritition for win xp and make another FAT32 partition if you want to share your data in win xp and ubuntu, and just install win xp on C:. Leave like 11GB of free space as unpartitioned, you will create the paritition on this free space in ubuntu instal.. After setting up win xp, boot up with ubuntu install cd, and make an ext3 linux partition from the install cd and 512 mb swap partition. 

good luck!

---

### Post by kanogil on 2005-07-15
Hello Everyone :) 

I'm sort of in the same situation as eeried:

I have an IBM Thinkpad R50e that came with Windows XP Pro pre-installed. I want to create a dual-boot system consisting of XP Pro and Ubuntu. I'm following this guide:

[https://wiki.ubuntu.com//WindowsDualBootHowTo](https://wiki.ubuntu.com//WindowsDualBootHowTo)   

When i start PartitionMagic in Windows, it displays the Windows-partition (if you need to know, it is NTFS) named "IBM_PRELOAD(C: )" and what I'm guessing is the notorious "hidden" IBM partition called "IBM_SERVICE(*.)" (according to PartitionMagic, this is a FAT type partition). The "IBM-SERVICE"-partition is located to the far right of the partition table.

( The reason I'm assuming that the "IBM_SERVICE" partition is the notorious "hidden" one, is that I can't see nor access it from Windows Explorer, even with administrator priveleges.)

Problem:

As for eeried, my laptop was not shipped off with an XP-install cd or an IBM system cd or similar. So I can't mess things up. I'm assuming that if I ruin my "IBM_SERVICE"-partition I will not be able to run Windows again, without off course getting an installation cd. Unlike eeried, I have no problems with the IBM resuce-password. 

I'm planning to rezise the "IBM_PRELOAD"-partition and create a root partition, a swap partition and a "datashare" partition between the two IBM-partitions. PartitionMagic lets me do this, and I'm only taking space from the "IBM_PRELOAD"-partition (in other words leaving the "IBM_SERVICE"partition exactly as it was.) To this point I've had no problems with resizing the "IBM_PRELOAD"-partition in the PartitionMagic-simulator I haven't litteraly created the partitions yet, so I don't know if I will encounter problems with the resizing yet.

Question:

Will everything be fine if I leave the "IBM_SERVICE"-partition exactly as it is on the partition table in PartitionMagic and create my linux-partitions between the two IBM-partitons as described earlier? Anyone who knows how PartitionMagic will behave on this issue?

I hope this is post is understandable. English is not my native language, so please excuse me if the text is hard to understand. I hope I've provided you with all the information you need, if not, tell me so and I will provide it.

Thank you all for being part of the wonderful Ubuntu-community :)

 Cheers,

Carl Martin :)

 PS: I'd love to have a pure GNU/Linux laptop, but I'm forced to have Windows because of certain educational based applications+++. I hope to replace them all with GNU/Linux equivalents on day, but that is another story ;)

---

### Post by javiadip on 2005-07-16
[QUOTE=kanogil]Hello Everyone :) 

I'm sort of in the same situation as eeried:

I have an IBM Thinkpad R50e that came with Windows XP Pro pre-installed. I want to create a dual-boot system consisting of XP Pro and Ubuntu. I'm following this guide:

[https://wiki.ubuntu.com//WindowsDualBootHowTo](https://wiki.ubuntu.com//WindowsDualBootHowTo)   

When i start PartitionMagic in Windows, it displays the Windows-partition (if you need to know, it is NTFS) named "IBM_PRELOAD(C: )" and what I'm guessing is the notorious "hidden" IBM partition called "IBM_SERVICE(*.)" (according to PartitionMagic, this is a FAT type partition). The "IBM-SERVICE"-partition is located to the far right of the partition table.

( The reason I'm assuming that the "IBM_SERVICE" partition is the notorious "hidden" one, is that I can't see nor access it from Windows Explorer, even with administrator priveleges.)

Problem:

As for eeried, my laptop was not shipped off with an XP-install cd or an IBM system cd or similar. So I can't mess things up. I'm assuming that if I ruin my "IBM_SERVICE"-partition I will not be able to run Windows again, without off course getting an installation cd. Unlike eeried, I have no problems with the IBM resuce-password. 

I'm planning to rezise the "IBM_PRELOAD"-partition and create a root partition, a swap partition and a "datashare" partition between the two IBM-partitions. PartitionMagic lets me do this, and I'm only taking space from the "IBM_PRELOAD"-partition (in other words leaving the "IBM_SERVICE"partition exactly as it was.) To this point I've had no problems with resizing the "IBM_PRELOAD"-partition in the PartitionMagic-simulator I haven't litteraly created the partitions yet, so I don't know if I will encounter problems with the resizing yet.

Question:

Will everything be fine if I leave the "IBM_SERVICE"-partition exactly as it is on the partition table in PartitionMagic and create my linux-partitions between the two IBM-partitons as described earlier? Anyone who knows how PartitionMagic will behave on this issue?

I hope this is post is understandable. English is not my native language, so please excuse me if the text is hard to understand. I hope I've provided you with all the information you need, if not, tell me so and I will provide it.

Thank you all for being part of the wonderful Ubuntu-community :)

 Cheers,

Carl Martin :)

 PS: I'd love to have a pure GNU/Linux laptop, but I'm forced to have Windows because of certain educational based applications+++. I hope to replace them all with GNU/Linux equivalents on day, but that is another story ;)[/QUOTE]


I have only used PartitionMagic once, but you should be fine as long as you dont touch the IBM's service partition. just to be on safe side, i suggest you make a backup of your current windows by using IBM Rapid restore onto a CD/DVD or usb hard drive and also make a IBM rapid restore rescue CD in case if anything gets messed up, you can always boot up with that CD and restore your windows image. If you dont have IBM rapid restore, download it from IBM's drivers and downloads sections, its a free download. 

As far as the resizing of your disk goes, say if you want 15 GB for your windows partition, just resize C: to 15 GB and make another parititon of remaining space using PartitionMagic. After doing this, boot up your laptop with ubuntu install cd, and edit the partitions from there so that now you have partition for linux (ext3), data drive(fat32) and swap. I would have 512 mb swap. I would keep like 12-15GB space for ubuntu. make sure you make the data drive partition as FAT32 if you want the read/write access from linux. 

As far as the speed and everything, ubuntu runs fine on my IBM Thinkpad R52, i didnt had any problems installing any hardwares. 

if you need any more help, just ask  :)

---

### Post by aveline on 2005-07-16
[QUOTE=javiadip]I have only used PartitionMagic once, but you should be fine as long as you dont touch the IBM's service partition. just to be on safe side, i suggest you make a backup of your current windows by using IBM Rapid restore onto a CD/DVD or usb hard drive and also make a IBM rapid restore rescue CD in case if anything gets messed up, you can always boot up with that CD and restore your windows image. If you dont have IBM rapid restore, download it from IBM's drivers and downloads sections, its a free download. 

As far as the resizing of your disk goes, say if you want 15 GB for your windows partition, just resize C: to 15 GB and make another parititon of remaining space using PartitionMagic. After doing this, boot up your laptop with ubuntu install cd, and edit the partitions from there so that now you have partition for linux (ext3), data drive(fat32) and swap. I would have 512 mb swap. I would keep like 12-15GB space for ubuntu. make sure you make the data drive partition as FAT32 if you want the read/write access from linux. 

As far as the speed and everything, ubuntu runs fine on my IBM Thinkpad R52, i didnt had any problems installing any hardwares. 

if you need any more help, just ask  :)[/QUOTE]
 if you use partition magic do NOT tell it to make the linux partitions into Ext2 or Ext3 partitions...for some reason PM *any version afaik* screws up the #'s and linux can't use or read the partitions...so instead to make some free space & tell ubuntu to use the largest free space partition it can find or manually partition things in the ubuntu installer.

aveline

---

### Post by kanogil on 2005-07-16
Hello again, everyone.

Thank you for your quick and very helpful posts :)

I have made a complete backup of my XP system using the IBM Rapid Restore application as you suggested, javiadip. 

When I open PartitionMagic, the partitiontable looks like this:

[[IMG]http://img228.imageshack.us/img228/6565/defaultpartition0ea.th.jpg[/IMG]](http://img228.imageshack.us/my.php?image=defaultpartition0ea.jpg)

Following the guide mentioned in the previous post, as well as listening to your advise, averline, I'm planning to do the following steps:

1. Create a "FILESHARE" FAT32-partition between the two IBM-partitions, taking space from the IBM_PRELOAD-partition and leaving the IBM_SERVICE-partition exactly as is. 
2. Resize the "IBM_PRELOAD"-partition down to selected size (roughly 10,5 GB), leaving lots of unallocated space between "IBM_PRELOAD" and the "FILESHARE"-partition.
3. Format the unallocated space with the Ubuntu-installer, and create an ext3-partition for Ubuntu and maybe a swap partition.
 
I belive this to be the correct setup: (NOTE: I haven't litteraly applied the changes yet.):

[[IMG]http://img228.imageshack.us/img228/1623/plannedpartition0ya.th.jpg[/IMG]](http://img228.imageshack.us/my.php?image=plannedpartition0ya.jpg)

Questions:

1. Is the setup shown above correct? Am I all set to write the changes to my drive?
2. I have 1 GB of RAM. Should I create a swap-partition, and if so, how big should it be? 

Cheers,  Carl Martin :)

---

### Post by javiadip on 2005-07-16
[QUOTE=kanogil]Hello again, everyone.

Thank you for your quick and very helpful posts :)

I have made a complete backup of my XP system using the IBM Rapid Restore application as you suggested, javiadip. 

When I open PartitionMagic, the partitiontable looks like this:

[[IMG]http://img228.imageshack.us/img228/6565/defaultpartition0ea.th.jpg[/IMG]](http://img228.imageshack.us/my.php?image=defaultpartition0ea.jpg)

Following the guide mentioned in the previous post, as well as listening to your advise, averline, I'm planning to do the following steps:

1. Create a "FILESHARE" FAT32-partition between the two IBM-partitions, taking space from the IBM_PRELOAD-partition and leaving the IBM_SERVICE-partition exactly as is. 
2. Resize the "IBM_PRELOAD"-partition down to selected size (roughly 10,5 GB), leaving lots of unallocated space between "IBM_PRELOAD" and the "FILESHARE"-partition.
3. Format the unallocated space with the Ubuntu-installer, and create an ext3-partition for Ubuntu and maybe a swap partition.
 
I belive this to be the correct setup: (NOTE: I haven't litteraly applied the changes yet.):

[[IMG]http://img228.imageshack.us/img228/1623/plannedpartition0ya.th.jpg[/IMG]](http://img228.imageshack.us/my.php?image=plannedpartition0ya.jpg)

Questions:

1. Is the setup shown above correct? Am I all set to write the changes to my drive?
2. I have 1 GB of RAM. Should I create a swap-partition, and if so, how big should it be? 

Cheers,  Carl Martin :)[/QUOTE]

Hello again,

First of all, I would give little bit of more space to windows, make it like 15 GB. And also give more space to data disk, coz you wouldnt need about 40GB of space for linux. I think 20 GB is more then enough. 

yes the setup looks good, I have a 1 GB swap parititon, but 512mb should be enough.

---

### Post by brim4brim on 2005-07-16
[QUOTE=javiadip]Hello again,

First of all, I would give little bit of more space to windows, make it like 15 GB. And also give more space to data disk, coz you wouldnt need about 40GB of space for linux. I think 20 GB is more then enough. 

yes the setup looks good, I have a 1 GB swap parititon, but 512mb should be enough.[/QUOTE]
 I was going to post similar, leave windows a good bit of space, most of the Linux programs are pretty small anyway so you shouldn't have any problems with hd space.  

As for hardware IBM always has good support for Linux I think, they like it a lot.

As for your partition magic leave it as unallocated boot from Ubuntu install and when you get to the partition feature select the one that automatically uses your unallocated space and splits it for a swap partition and the main partition for Linux.

---

### Post by kanogil on 2005-07-16
Thanks everyone :)

Just one more questiton:

I have a quite big music collection, around 20 GB or so. Would it be wise of me to make the "FILESHARE"-partition big enough and have that be a place for my media, so I could read/write to it with both Operating Systems? (correct me if I've misunderstood something) What would be the pros/cons of this?

cheers, Carl Martin :)

EDIT: I see that my question is partially answered in your post, javiadip ;)

---

### Post by javiadip on 2005-07-16
[QUOTE=kanogil]Thanks everyone :)

Just one more questiton:

I have a quite big music collection, around 20 GB or so. Would it be wise of me to make the "FILESHARE"-partition big enough and have that be a place for my media, so I could read/write to it with both Operating Systems? (correct me if I've misunderstood something) What would be the pros/cons of this?

cheers, Carl Martin :)

EDIT: I see that my question is partially answered in your post, javiadip ;)[/QUOTE]

yes that would be ideal, thats what i have right now, I have all my music on my data drive so its sharable on linux and windows.

---

### Post by eeried on 2005-07-17
Hello everybody,

I didn'y see all your replies until now -- didn't get any notice in my email client; 

Never mind. it all worked like a charm!


The only difficulty was guessing the files that got stuck at the  end of the C partition was simply WinXP swap file (I got that hint on the Lurkhere forum for WinXP).

So I disabled the swapfile in WinXp > System, and defrag again.

Then I used knoppix Live CD and Qtparted to resize the Win partition -- hda1, while hda2 was the hidden IBM partition -- It was more reassuring than doing it while installing Ubuntu, i thought.

I was then able to reboot and check how WinXP took this resizing. Very well apparently. I then restored some kind of swap file on WinXP.

WinXP and IBM  complete with all the GNU/GPL apps I installed took up 8 GB on the C: partition, so I allowed 4 GB more for users' files, and therefore have ample space for ubuntu and another distro I'll install later for the fun of it.

Partitionning with ubuntu partman was just great -- The Ubuntu team did a great job because partman is so sophisticated and flexible, and there are so many options, but you can't really make a  silly mistake. I was able to partition the free space created by Qtparted just as I pleased : swap, /, /home, /usr/local, /tmp, /var/www, and all as reiserfs, except for the swap of course.

Conclusion 1: Why would you use partition magic when there's that great GNU/GPL tool Qtparted which BTW works better on Windows partitions than on Linux partition!

Conclusion 2: No need to reformat your HDD, or reinstall WinXP according to my experience.

Conclusion 3: My only failure: the dial-up connection doesn't work at all -- though it worked  on the ubuntu Live CD.

Perhaps this is because I forgot to plug the cable from the laptop to the phone plug in the wall before installing ubuntu. The modem is inside the box, and works fine with Linux.

I configured the connection with pppconfig, and chose PAP, and maybe chose the wrong port -- I'll have to check the COM number on the windows side perhaps.

Any suggestion?

I'm so pleased not having to use WinXp at all while I can use this laptop which was kindly lent to me for the summer.

Cheers,

---

### Post by vedro on 2005-07-18
ellow....

I own an R40 to and my modem work ok.. It was recognised at installation. maybe because I wave chosen an expert installation. By the way, I have totaly erased/formated the harddrive, so I have no longer any hidden partitions. This has resulted that Access IBM button an computer startup doesnt worl anymore like it should but I don`t give a damn because I will never install window on that machine again. With Kubuntu I can do anything that I was doing with windows (XP and 2003 Server)  :razz: 

Hmm....your modem problem is puzzling me.. You said that your modem is recognised by the system? or not? Maybe you got IRQ resources mixed... Did you turned off the option: "Wait for dial tone before dialing"? On this option everbody forgets sometimes.. me too  :grin: 

have a nice day, 
vedro

---

### Post by eeried on 2005-07-18
Many thanks for your post vedro!

After reading several threads I'm beginning to suspect the thinpakpad modem is a winmodem. it seems to be AC'97.

The COM port being 3 in Windowze I set pppconfig /dev/ttyS2.

No the modem was not recognized during installation, and neither the pon command or the connxion through Gnome-ppp works.

Well, I started a new thread on the subject.

Good to know your modem works fine :wink: !

---

### Post by WildTangent on 2005-07-19
for anyone that might have gotten the idea to install XP on a FAT32 partition, DONT! ever wonder why your filesystem had to be checkec when the power went out, or you hit the power button on your old windows 98 computer? FAT is why. NTFS is somewhat like a journalled filesystem like EXT3 (although not as advanced), it records actions so that if writing to disk is interupted, it can revert back to what it was before. just thought i should add that for you all

-Wild

---

### Post by novoa4 on 2006-08-08
To remove this hidden partition from your R40 or any thinkpad:

Power on the Laptop
Press Access IBM button, select F1 and Choose “Start Setup Utility”
Choose Security->IBM Predesktop area and change settings to disabled, Select Yes, continue. (Note that this step is important, otherwise your will not abe ablt to delete this hidden partition.) 
Press F10 and save and exit.

Now Windows and Ubntu will seee this partition as Fat32 Partition, that you can delete. Note this partition has the Preloaded restore image for your thinkpad. If you delete it, you will need to obtain the Restore CDs from IBM (Lenovo)

---

