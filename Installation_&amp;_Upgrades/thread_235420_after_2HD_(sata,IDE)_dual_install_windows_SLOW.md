---
title: "after 2HD (sata,IDE) dual install windows SLOW"
date: 2006-08-13
forum: Installation &amp; Upgrades
---

### Post by strebor71 on 2006-08-13
Hello all,
So i successfully installed the new dapper drake to a 20gig IDE drive, after having installed windows 200pro on a 160gig sata dive.
originally the sata was the sole drive in the system. i then installed the ide drive and switched the boot order so that the ide drive booted first, (per [http://www.ubuntuforums.org/showthread.php?t=46003&highlight=dual+boot+sata](http://www.ubuntuforums.org/showthread.php?t=46003&highlight=dual+boot+sata) ) which was very helpfull i might add. great work herman on your site as well, very helpfull and informative. grub works perfect all is well . . . untill i boot into windows 2000. the computer takes forever to get to the login screen. and after that all operations are slowed down significantly. i tried to go into disk management to see what windows thgought of the new drives and lists them but does not give thewm a drive letter. should i assign one to them? i think its all slow becoause windows just doesnt know what to make of them? any advise would be appreciated. -mike

---

### Post by Herman on 2006-08-13
Hello, strebor71, and welcome. 
I have no experience with more than one hard drive per computer myself, I have read about all kinds of arrangements though, It should work okay having Windows on the second drive as long as it will boot up alright. I have not read of a Linux install slowing Windows down at all before. It might have something to do with swapping your drives around though. Maybe it just needs a re-boot or two and maybe running some maintenance utilities will help. If not, maybe someone who has made a similar arrangement will come along here with some Windows multi-disk know-how.

If you have a seperate FAT32 data sharing partition, you should try to get that recognized by Windows. If it hasn't appeared in 'My Computer' automatically, probably you can go into 'Disk Management' and re-format the FAT32 partition from the Windows side. Then it should recognise it. You'll see it appear in 'My Computer' , probably after a reboot.  
I wouldn't bother with trying to get Windows to recognise any Linux partitions though, unless you install one of those special drivers so Windows can recognize ext3 filesystems  format.
I'm glad you found my website helpful, strebor71, and congratulations on a successful dual boot install.

Let me know if you do have a FAT32 partition and you have too much trouble with getting it recognised. If you need help I'll make a FAT32 partition and go run through the procedure myself to make sure I get the instructions right and then I'll help you with it.
Regards, Herman :D

---

### Post by strebor71 on 2006-08-13
thanks for the reply herman, i currently do not have a fat32 partition, other than what the guided partitioning creates during initial install. ubuntu is installed on a 20gig drive all by itself so there is plenty of room for another partition. what would be the resaon that i would want or need a fat32 partition? just a place for shared storage? 
i am going to experiment with swapping around the boot order of the drives and see if i can get the sata drive to be the first boot device while having the ide connected as well. didnt have much luck with that as i recall however. this is my first board with sata capability and it is a rather picky one at that (asus p4r800). i vaigly remember that after switching to the sata drive i wanted to keep the orig. ide drive in the computer for storage or as a linux drive, and i had to unhook it because it was having the same issues. so i dont think that it is a linux/dual boot problem but more a configuration problem with the hardware. 

would i be better off doing away with the second drive all together and put linux onto the sata drive? are there advantages/disadvatages to having 2 drives? thanks again -mike

---

### Post by KGWagner on 2006-08-14
Windows will not recognize drives formatted as anything but one of the FAT or NTFS types, That's why you're not seeing them when you're in Windows.

As far as the slow boot goes...not sure on that one. Did you reset your boot order after the install? If not, BIOS will look at each device in order and wait for it to fail until it finds something bootable. That wouldn't explain why Windows itself was slow, though. Although, perhaps you're getting used to Linux and finally seeing what a dog Windows is <grin>

---

### Post by Herman on 2006-08-14
>  what would be the resaon that i would want or need a fat32 partition?  I don't have one, I have Windows XP with FAT32 anyway, and I can open Windows files and alter them with Ubuntu apps, or paste files into Windows from Ubuntu. 
If I had NTFS filesystem in Windows, which seems to be popular these days, I would not be able to 'write' to the Windows partition from Ubuntu, but I could 'read' from it only. The NTFS filesystem can be damaged by attempting to 'write' to it from Linux. Although, I have read that now great progress has been made in this respect, and it will not be much longer before it will become common practice. At this stage, though, it is still not recommended.
For that reason a seperate FAT32 partition that both operating systems can read and write to is often used for sharing common files in dual boot computers where Windows has NTFS.

>  would i be better off doing away with the second drive all together and put linux onto the sata drive? are there advantages/disadvatages to having 2 drives? thanks again -mike I don't know. I think there are all kinds of different disk and partitioning arrangements and it's really up to the individual to decide what it best for them. Anything should be okay. I only have single hard disk computers, but I want to get some more hard disks just to experiment and play with them and gain experience. Regards, Heman :D

---

### Post by strebor71 on 2006-08-14
> **KGWagner said:**
> Did you reset your boot order after the install? If not, BIOS will look at each device in order and wait for it to fail until it finds something bootable.
I dont think that i am supposed to reset the boot order, that would put the sata drive to boot first and then it would bypass the grub altogether and boot to windows. I kind of like the fact that install left my sata drive completely as it was, so no need to deal with mbr problems. (a check in the pro column for 2 hard drive dual boot).

After a few re-boots to each OS (plus the automatic disk check that poped up a few times booting to windows cuz it doesnt know whats up with the linux drive) the system is running smoother.

I think though that i have decided to leave the desktop windows for now, yank the ide drive, and put either kubuntu or ubuntu onto my laptop dual boot with xp pro. however there is another not so typical situation here that i would like some help with. a short review of the history of my laptop is needed, please bear with me) the laptop originaly had a 60gig drive - all sorts of problems with the drive cable and bla bla bla. the drive died, and couldnt be recovered. while waiting to get a new drive from ebay . . i re-installed xp onto a spare 4 gig laptop drive that i had. i then got the new drive but had lost the xp install disk so i installed windows 2000pro. i then got smart and successfully (with the help of a laptop hard drive adapter, to plug the old 4gig drive into my desktop) created an image of the drive with ghost, then used gparted live cd to split the new 60gig drive with win2k pro in half. Then using ghost again, restored the image of xp pro i created, onto the second partition. modified the boot.ini of each system and PLUNK! i had a dual boot with win2k and xppro. rather sneaky i thought to myself as i hurt my arm patting myself on the back. . . so therein lies the potential problem/non-issue, but might work out rather nicely question. because xp is on the second partition will this be an issue with the install of ubuntu not recognizing it? or it doent matter as long as its not on the same partition? also after having read the section of hermans guide that states, and i quote (props to herman here)
> "Actually, there are several advantages in resizing the Windows partition from the beginning of it and installing Ubuntu in front of it instead. That's a lot easier to do with GParted LiveCD before beginning your install."
so havent i effectivly already done this step by the way i have my system set up? if not please explain what the difference would be, aside of cource that its one large ntfs partition. can't i just run the install and select the first partition to put linux on and partition it as i see fit? either way it will be fun to experiment.
 also i would like to take hermans advice on creating a small partition at the end of the drive to create a backup of my new install (if it works that is) but im in the dark as to actually how to create the backup itself. (sorry for not including a link to that section herman i tried finding it but cant seem to find where i read it.) i will create a 2gig space for it and when im done and happy with my install, by then i will hopefully have gotten wise as to how to actually create the backup.
i realize that this is becoming more of a novel than a reply, but i'm hoping that at least some of this can be applied to other installs to help someone. and to herm and others offering their time and advice on this forum, hats off =D> , without the wealth of open armed assistance and instruction that you provide, there would be a lot less people becoming slowly but surely transformed into ubuntu faithfull. it can be rather frustrating at times when you cant get linux to do something that you know it can do, especially when you know that all you have to do is boot to windows and do it there. and the support you provide is the reason many of us do  stick it out and try to become proficiant linux users.
  that said . . .  I am having a hard time deciding which invironment to go with, kde or gnome. i did notice that with kubuntu there was a wireless config tool installed by default, and i cant seem to find it in ubuntu? although im sure it can be installed if it isnt already. i want to put linux onto the laptop to take advantage of all of the cool new open source wifi apps. and use my laptop as a portable powerfull wireless network troubleshoot/inspection/setup tool. are there advatages to either kde or gnome for that sort of usage?
                            wheew . . thanks again, i will be looking forward to any advise given or thoughts shared. -mike

---

### Post by confused57 on 2006-08-15
I've never used it, but PartImage may be what you need for creating a backup:
[http://psychocats.net/ubuntu/partimage.html](http://psychocats.net/ubuntu/partimage.html)

---

### Post by strebor71 on 2006-08-15
Cool, that looks like what i can use. And then after i read your post, i thought to myself, why dont i just use ghost as i did with the xp image i created. i am wondering if i can do this executed through windows xp, backing up the patrition(s) of linux. anyone have any experience with ghost images and linux?

---

### Post by Herman on 2006-08-15
> also i would like to take hermans advice on creating a small partition at the end of the drive to create a backup of my new install (if it works that is) but im in the dark as to actually how to create the backup itself. (sorry for not including a link to that section herman i tried finding it but cant seem to find where i read it.) i will create a 2gig space for it and when im done and happy with my install, by then i will hopefully have gotten wise as to how to actually create the backup. Hello, strebor71, 
All I do to make a backup of my operating system and all installed software and settings is move all the regular data out to another drive. Then when my /home/username directory is empty of regular user data I boot my GParted LiveCD. I resize the partition to as small as it will go. (Around 2.3 GB maybe).  I make sure there is enough free space at the end of my disk. Then I just copy and paste the whole operating system with GParted. It's so simple that no instructions are really necessary. It will take ten or fifteen minutes to copy and paste about 2.4 GB or so of software. The reverse to restore if I 'hose' my system. It only takes a few minutes to move the data back from my USB disk. Mostly I just leave it on the USB disk and only move back the things I need when I have to.

Aysiu's Partimage should be good too, Use whichever suits you. I think aysiu has very excellent knowledge and advice and he's a good writer too. I have some different notions, but basically I agree with aysui on 99% of topics.

Moving Windows towards the end of the disk and then installing Ubuntu in front of it could be a good idea, or maybe it isn't too important. The main advantage of doing that (having Ubuntu in front of Windows), is so that it is easy to resize whenever we want after that . However, I have read that when GParted 0.3 comes out, we will be able to move Linux partitions too. I don't know how far in the future that will be , but it might not be too far away. 
 Providing the Windows partition number is not changed it should be okay. It works for me without any problems. Do Not copy and paste Windows though, only Linux. With Windows it is best to 'move' it, so that the partition number will not be changed. Otherwise Windows will be unbootable and will say .hall is missing or something, so I have read. It can be repaired if it's FAT32, but it is very tricky to fix it, especially if you have NTFS.  So be carefull if you do try that.

All the best, Regards, Herman :D

---

### Post by kopo88 on 2006-08-15
If you still want to try to fix the slow Windows problem:

Adding or removing physical drives in Windows can inexplicably screw up the IDE channels. One or more of your channels may have been set to PIO instead of DMA, which is much slower.

Right click on My Computer > Properties > Device Manager > IDE ATA/ATAPI Controllers.

For primary and secondary IDE channels, check the Advanced Settings to see if any of the "Current transfer mode" boxes say "PIO mode." If so, try toggling everything to "DMA if available," pressing OK, and checking again.
If this doesn't work, try removing the IDE channels and rebooting to let Windows redetect them. One caveat here is that I don't know whether you can remove the primary IDE channel (which usually runs your hard drives) while still running Windows. Might want to Google about this.

Good luck.

---

