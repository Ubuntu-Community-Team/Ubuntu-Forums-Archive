---
title: "Partitioning for Ubuntu install"
date: 2011-11-05
forum: Installation &amp; Upgrades
---

### Post by iridemybike on 2011-11-05
Hi everybody, just starting out with Ubuntu and I've been reading the documentation and I'm a little confused on the best way to go about partitioning to install Ubuntu. I'm going to be installing the latest version 11.10 and attempting to dual boot with Windows 7 Home Premium 64bit on a single disk drive on my laptop. I would really prefer not to have to wipe out Windows 7 to do this and it seems like I don't have to but I'm not sure the best way to go about creating the blank partition before I install Ubuntu. 

I'll be working with C drive which currently contains only Windows 7. The main partition is 448gb and I have 312gb free. I'd like to create 20 - 30gb or so(however much would be appropriate for Ubuntu and whatever tools and applications it's going to need. 

What would be the best way to go about partitioning for Ubuntu without wiping out Windows 7 and starting all over to be able to dual boot with my set up?

---

### Post by Hakunka-Matata on 2011-11-05
Hi, and Welcome to the forums.

Win 7 being your resident os, you must take caution to use Windows tools, like Diskmanager to work with Windows Partitions.

[LIST]
[*]boot to win7, use diskmanager to display your current partitioning scheme, if you can take a snapshot and post that, that would be great.
[*]Once you have made room on the HDD by shrinking, and doing a few other things, (it depends on whether or not you already have four primary partitions on the HDD) then you can boot to the Ubuntu liveCD/USB and "Try Ubuntu without installing"
[*]from there you can prepare the HDD further by creating partitions in the unallocated space you've made available.
[/LIST]

****************************************
from **oldfred** post: more good information:
 				 				**Re: Harddisk not bootable because of GRUB?** 			
 			 			 		   		 		 		I still like gpt, but if you want to remove it. But once you have partitions set up you should be ok whether gpt or MBR.

Because the gpt has backups, some times it does not get totally housecleaned. You need to use gpt tools to houseclean the gpt.

GPT & MBR are types a partitioning a drive. NTFS &  FAT for  Winodws and  ext3, ext4 etc for LInux are types of formats for the  partitions.

FixParts is the easiest way to remove the stray GPT data. GPT fdisk  (gdisk or sgdisk) can do it, but the procedure's a bit more involved.
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)
You then need to use gdisk to convert from gpt to MBR
[http://www.rodsbooks.com/gdisk/mbr2gpt.html#gpt2mbr](http://www.rodsbooks.com/gdisk/mbr2gpt.html#gpt2mbr)
Converting from MBR to gpt:
[http://ubuntuforums.org/showthread.php?t=1454252](http://ubuntuforums.org/showthread.php?t=1454252)

Use parted or gparted to remove gpt if no data to save:
[http://ubuntuforums.org/showthread.php?t=1719851&page=2](http://ubuntuforums.org/showthread.php?t=1719851&page=2) post #20
[http://www.sevenforums.com/tutorials...-mbr-disk.html]("http://www.sevenforums.com/tutorials/26203-convert-gpt-disk-mbr-disk.html")
 		                   		  		  		 		 			 				__________________
				[COLOR=Navy]Let us know what works and to mark your thread as[/COLOR] [[SOLVED]]("http://ubuntuforums.org/showthread.php?t=878683")[COLOR=Navy], use [COLOR=Red]Thread Tools[/COLOR] on forum page. 
Howto: [https://wiki.ubuntu.com/UnansweredPo.../SolvedThreads]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads")[/COLOR]

---

### Post by iridemybike on 2011-11-05
Here is the current partitioning scheme, I ran the disk cleanup and defrag a few days ago but will run them again before starting any partitioning and install. 

Couldn't get the picture itself to post so here is the link to it. 
[B]
[http://tinyurl.com/3vbm82z](http://tinyurl.com/3vbm82z)[/B]
[IMG]https://picasaweb.google.com/lh/photo/lE-Wf5FPVoe1p2Ul1H4hU0B70t6o1gZF2GB092Eap-o?feat=directlink[/IMG]

---

### Post by Hakunka-Matata on 2011-11-05
OK, you have four primary partitions already, you know that is the maximum for an MBR HDD, right?
You'll have to delete at least one of them.

Do you have a Rescue disk for win 7?  and whatever else backups you need in case Mr. Murphy shows up on the scene?

---

### Post by oldfred on 2011-11-05
Definitely make Windows repairCD and backups of Windows as Hakunka-Matata suggests:

Good advice on how to handle all four primary partitions used. - srs5694
[http://ubuntuforums.org/showthread.php?t=1686440](http://ubuntuforums.org/showthread.php?t=1686440)
Besure to create recovery DVD(s) first. And a Windows repair CD.
HP tools partition discussion - similar for other vendor partitions:
[http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360](http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360)
Shrinking a Windows 7 partition is best done in Windows. [B]
But do not create new partitions with Windows.[/B]
[http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/](http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/)
The Hedge show graphically how to delete & create partitions:
[http://ubuntuforums.org/showthread.php?t=1713649](http://ubuntuforums.org/showthread.php?t=1713649)

Backups ---------
The vendor recovery DVDs are just an image of your drive as purchased. If you have housecleaned a lot of cruft normally included, run many updates with many reboots, and added software you may want a full back up.
Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=1626990](http://ubuntuforums.org/showthread.php?t=1626990)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

Make your own Windows recoveryCD/repair:
[http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc](http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc)
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

---

### Post by iridemybike on 2011-11-05
Ok, thanks for the help! Looks like I have some backups and recovery discs to make in the next few days. I guess I'm going to have to break down and buy some blank dvd's afterall! Thanks guys!

---

### Post by iridemybike on 2011-11-11
Ok, got my blank dvd's and finished making all my backups and recovery cd's....finally...nothing like playing human cd changer for 5 hours! 

I've been reading the links you guys posted for me and while I'm debating which one of these partitions I'm going to kill off I noticed that I need at least 2 partitions in Ubuntu, 1 for the os itself and another small one for something called swap. So does this mean I actually need to get rid of 2 of my partitions or more? Or does swap become a partition inside the one I create for Ubuntu?

---

### Post by darkod on 2011-11-11
No, you need to delete only one. The max is 4 primary (which you have got) or 3 primary and 1 extended which can have more logical partitions inside it.

So the end result would be 3 primary + 1 extended with 2 partitions for ubuntu inside (or even 3 if you want separate /home).

However, take into account that only deleting a partition is not enough if you want to allocate to ubuntu more than that partition has got. You still have to shrink C: a bit to have more unallocated space on the HDD.

---

### Post by iridemybike on 2011-11-11
Ok, got it, I assume the partition for swap and home are created during the Ubuntu install and not from Windows correct? I should only be getting rid of one of the partitions to create unallocated space from Windows? 

Right, Planning to shrink C to get about 30gb for Ubuntu. 

Now I just have to figure out which one of the partitions to get rid of, Just not sure which one will cause the least disruption to using the laptop in Windows....

---

### Post by oldfred on 2011-11-11
See post #5 for alternatives. Do not delete 100MB boot/repair nor c:. With backups the other two become less important.

Do not create partitions in Windows as it will convert to dynamic and you may not be able to convert back.

---

### Post by iridemybike on 2011-11-11
Ok, so it looks like HP_Tools is the winner for which one gets to be deleted to free up a partition. With the current scheme in my screenshot above the plan would be to get rid of the HP_Tools partition(I've already turned off the HP support assistant updates to keep it from restoring itself) in Windows, Shrink C by 30,750mb but don't format anything to keep it as unallocated space. Then in the Ubuntu install I need to go with the manual option and create the partition for the unallocated space for the ./ root for Ubuntu, 8gb for the ./swap and ?? for ./home. Anything I'm missing here? Is that enough space for everything? Something I should be doing differently? 

I know it's a lot of questions, just don't want to miss something and turn my laptop into a paperweight...I need windows to be functional throughout the process to keep working!

---

### Post by oldfred on 2011-11-11
If you are only allocating 30GB which is fine, I might keep /home inside / (root) so space is shared in one partition. (But that is not my standard recommendation.) At this time you do not know how much you will store where. I also would not make swap 8GB unless you hibernate and with Ubuntu there is little reason to hibernate. I do prefer for both Windows & Linux smaller system partitions & larger data partitions.

This is my standard suggestion and whatever you do is not critical as long as you backup any of your data as you can easily reinstall.

For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home:
1. 10-20 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext4(or ext3)
3. 2 GB Mountpoint swap logical

Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.

After you shrink Windows, reboot it once or twice as it will want to run chkdsk to update itself. Best to do before installing Ubuntu.

---

### Post by iridemybike on 2011-11-12
Ok, got my primary partition freed up and left it as unallocated space.  About to start install and just want to make sure I understand it right.  

I have 30GB unallocated space now and 1 free Primary partition

Inside of that I need at least 2GB mountpoint logical for swap
28GB mountpoint logical in ext4 for the Ubuntu itself.

I'm just not sure what to do with /home. What is /home and how big should it be? I'm not familiar with the Ubuntu file system so I tried searching but couldn't find anything explaining it, maybe I just wasn't looking for the right thing. Seems it should take up some part of the remaining 28GB if I understand correctly.

---

### Post by Hakunka-Matata on 2011-11-12
separate partition for /home is a method that preserves your data (&settings) in a separate partition from the / (root) partition.  The / partition contains the OS itself.  This way, when you mess up the OS, or want to change to a different Release, you can do a new install to your / partition, and not lose any of your data.

Look at oldfreds post # 12, he explains it very well.   With that method you'd only have ~8GiB left for a /home partition, not much.  You could make your / partition smaller, like maybe 10GiB, that would free up 10GiB more for your /home partition.  You could also shrink the windows partition further, (if available), yadda, yadda, yadda,  look @ the partitioning link in my signature for Ubuntu's offical idea on partitioning.
You could also reduce the swap partition to 1GiB.  

You may want to adopt a mind set right now, if this suits your way of working:  Just install to the unallocated space, let Ubuntu do it all, see how it turns out.  Then do it over, and over, until you're comfortable with the procedure.  It only takes maybe 15 minutes (90% un-attended) time.

---

### Post by iridemybike on 2011-11-12
Ah, ok, now I understand /home. Good idea actually! Looks like I might create more unallocated space, I have plenty at this point. I'm guessing any applications I install for Ubuntu will go to the / partition and settings/documents/pictures/music etc goes to /home? Would I be able to access things like music and movies from the C: windows partition from Ubuntu or best to simply put them in cloud storage for that kind of thing? Just trying to figure out what's going to go where so I can figure out how big I really need to make the partitions. Thinking maybe 40Gb each for / and /home and 2Gb for swap...

---

### Post by darkod on 2011-11-12
Since you're new to ubuntu, and unless you plan to put major load of software on it, even 10GB is too much. Just to help you understand, my install of 11.10 with added Netbeans development IDE and Oracle JDK7, is about 3GB. Take into account that linux software usually doesn't need as much space as windows software.

As far as accessing windows partitions go, you can access all NTFS partitions from ubuntu. But the opposite is not true, windows can't see linux partitions (not by default).

---

### Post by iridemybike on 2011-11-12
Ok, that helps at lot. I don't know how much software I'll end up loading for it but I'd rather have too much space than not enough, some sort of Office equivalent and web browsing at the minimum. I keep most of what I use online anyways just because I'm away from the laptop so much and I need to be able to access it all from my phone. Being able to access the documents/music/movies etc from the NTFS partition will save a lot too. I can always save anything I create in Ubuntu online to get around not being able to see Ubuntu partitions from windows.  So just to be safe while I have the free space to work with I could do 15 GB for / 15Gb for /home and 2GB for swap. I don't use hibernate at all. The laptop boots plenty fast for me.

---

### Post by darkod on 2011-11-12
15/15/2 is a good plan. Just to remind you about the Office and browsing that within Ubuntu (within those 3GB) you already have Firefox and Libre Office package.

---

### Post by iridemybike on 2011-11-12
Ok! Thanks for the help guys! I know I'm just full of questions over here but without you guys I'd have probably jumped in and bricked my laptop by now so thanks a lot! Going to give it a shot and see how it goes!

---

### Post by iridemybike on 2011-11-12
Just wanted to let you guys know I got everything installed and it went great! I'm writing this from Firefox in Ubuntu now! Off to bring firefox current and get everything working the way I like. Thanks for the help guys!

---

### Post by darkod on 2011-11-12
You are welcome, glad you got it running. Please mark the thread as Solved, you can do it in Thread Tools above the first post on any page.

---

