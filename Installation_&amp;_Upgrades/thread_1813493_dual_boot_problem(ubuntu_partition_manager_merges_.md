---
title: "dual boot problem(ubuntu partition manager merges free space with recovery partition)"
date: 2011-07-27
forum: Installation &amp; Upgrades
---

### Post by weezilla on 2011-07-27
My purpose: dual boot windows 7 (preinstalled) with 11.04_64. 

Alright, I can't seem to find a solution to this issue. I've searched and troubleshot it. I have an HP DV7tqe laptop with windows 7 and 1 hard drive. It came with windows 7. I just recently shrank the OS partition by 100GB using the Disk Management tool in windows. I left the freed space as unallocated and rebooted into my Ubuntu 11.04_64 dvd. When I start the setup, I have two options: erase windows 7, or to set up partitions manually. I choose manually and it seems to list the unallocated space and the recovery partition together as one device.

Here is what is listed inside of the windows disk management tool:
199Mb - NTFS - can't remember name
483Gb - NTFS - OS/boot/page/etc
14.5Gb- NTFS - Recovery
103Mb - FAT32- can't remember
97.7Gb- unallocated - free space that I made

Here is what I see from the Ubuntu Partition Manager in the installer:
/dev/sda
  /dev/sda1 -      - 1MB
  /dev/sda2 - ntfs - 208MB
  /dev/sda3 - ntfs - 519430MB (used, 13795MB) [this used # isn't right]
  /dev/sda4 -      - 120493MB

I've also tried changing the partition type of the 97.7GB partition to FAT32 and NTFS to see if that helps linux separate it from the recovery partition, but that doesn't seem to work.

The problem is, I can't/won't install it over my recovery partition.

Any help would be greatly appreciated.

---

### Post by inertself on 2011-07-27
I would un-do (resize back) the partition work you did, and then let ubuntu "install alongside windows".  It will do the partitioning for you and you just select which windows partition (the one you already resized) for it to install to.  It should leave all other partitions alone. 

If you don't have the install alongside option (which you should...), not sure what version you are using but get the latest 11.04 version from ubuntu.com and stick it on a USB disk, it's a lot quicker booting up the live CD.

---

### Post by weezilla on 2011-07-27
I can resize it back, but shouldn't I have the option now to install along-side Windows? I don't have that option right now.

The reason I wanted to do it manually was so I could add a 10gig fat32 partition to share files between windows and linux.

---

### Post by weezilla on 2011-07-27
I expanded the partition back to its original state and ran the Ubuntu setup, but there is still no option to install alongside 7.

---

### Post by Hakunka-Matata on 2011-07-28
Ubuntu will happily read and write to NTFS partitions


if you are booted into liveCD natty, open a terminal window,  "Accessories Terminal", or "Ctrl - Alt - T"

use this command to display your hard disk partitions and sizes , 

```
sudo fdisk -l 
```  that's a lower case L

Here's an example of the output generated

> das@das-System-Product-Name:~$ sudo fdisk -l
[sudo] password for das: 

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0008047b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        2550    20482843+  83  Linux
/dev/sda2            2551        7649    40956928   83  Linux
/dev/sda3            7650       12748    40957717+  83  Linux
/dev/sda4           12749       30402   141800028    5  Extended
/dev/sda5           12749       15298    20482812   83  Linux
/dev/sda6           15299       17848    20482843+  83  Linux
/dev/sda7           30134       30402     2150400   82  Linux swap / Solaris
/dev/sda8           17849       20398    20480000   83  Linux
/dev/sda9           20398       22948    20480000   83  Linux
/dev/sda10          22948       30134    57719808   83  Linux

Partition table entries are not in disk order



---

### Post by Quackers on 2011-07-28
You already have 4 primary partitions. This is the maximum number available.
You need to delete one primary partition (probably the HP TOOLS one) then shrink your Windows partition in Disk Management screen (after defragmenting it) then you can boot from the Ubuntu live cd/usb and the option to install alongside will be available.
I would still recommend that you create the required Ubuntu partitions manually though (as logical partitions, NOT primary partitions).
That way you get to choose what happens.

---

### Post by weezilla on 2011-07-28
Thanks much quackers, and my other friend. I'll do some quick reading about deleting this tools partition, and hopefully give it a whirl. 

Glad there's a reason for this :) There should be a note in the installation process. It's strange it combined those two partitions when viewing them.

Thanks !

---

### Post by Quackers on 2011-07-28
You're welcome :-)
The problem is not with Ubuntu. In fact, the Ubuntu installer has just stopped you making a mess of Windows!
The problem is that some manufacturers now insist on using all 4 primary partitions by default.
May I suggest a strongly worded letter to your pc's manufacturer, thanking them for tying your hands :-)

---

### Post by weezilla on 2011-07-28
Thanks, I will write to them. For reference of anyone else with an HP DV7tqe (or similar laptop), here is a link which has information about the HP Recovery and tools partitions.

[http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360](http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360)

I need to get some sleep now, but I will disable the tools partition tomorrow and attempt my install. It will be really nice to run Linux stand alone instead of inside virtual box !

---

### Post by Quackers on 2011-07-28
If you haven't done so already, it is a good idea to make a set of recovery dvd's (or even more than one set) and also a repair cd, as you might need them.
The repair cd can be made via Control Panel > Backup & Restore Centre > then in the left pane "make a recovery cd" (which is what most of us call a repair cd).

Take your time and be careful :-)

---

### Post by Mark Phelps on 2011-07-28
> **inertself said:**
> I would un-do (resize back) the partition work you did, and then let ubuntu "install alongside windows".  It will do the partitioning for you and you just select which windows partition (the one you already resized) for it to install to.  It should leave all other partitions alone.

Do NOT, repeat NOT do this!!

This is an easy way to corrupt the Win7 OS partition and render Win7 unbootable.

If you don't have a Win7 Repair CD, and you can still run Win7, BEFORE you do anything else, boot into Win7 and use the Backup feature to create and burn a Win7 Repair CD.  That will allow you to repair the Win7 boot loader.

---

### Post by weezilla on 2011-07-28
Oh yes, I am being quite careful. I still need to make that repair cd. I made my recovery cd's using the HP Recovery manager last night whilst I couldn't sleep. I deleted the tools and recovery partitions and reshrank my OS partition by 100Gb. I left the space unallocated and booted into Ubuntu 11.04. Whether I choose Try or Install, the OS hangs; ctrl-alt-F1 does not work (it hangs it entirely, the mouse won't even move). 

Last night, I tried formatting 15Gb of it to a FAT32 that I would use for sharing, and 100Gb to NTFS (just to something other than unallocated). It let me into the partition manager (both gparted and installer), but it looks like it had merged the FAT32 partition with the NTFS space (and still called it FAT32). Furthermore, I had assigned a name of "shared" to the 15Gb FAT32. If I recall correctly, the "shared" name actually showed up formy 500Gb OS NTFS partition, although I am sure I gave it to the FAT32. 

There is also a 1MB partition which isn't listed in windows 7 disk manager. Is this counting as another Primary partition? I want to have that shared space, so it would be best to create two partitions for Linux, but I can't do that if there's already a 1MB, a system, and an OS partition by windows 

:(

Advice? Thanks much for your attention !

---

### Post by Quackers on 2011-07-28
The 1MB unallocated space is normal. It's a boundary that's used between partitions now.
If you deleted 2 partitions then formatted the unallocated space to NTFS and then made a new FAT32 partition, you are back where you started :-) 
You've got 4 (presumably primary) partitions again.

---

### Post by coffeecat on 2011-07-28
> **weezilla said:**
> Advice? Thanks much for your attention !

@weezilla, we really need to see what your partition layout is like now. I have a HP netbook so I'm familiar with the way HP arrange things (actually, it's not too difficult to get around it) but I can't follow what you've done.

Boot up with an Ubuntu live CD or USB and open a terminal and post the output of the command that Hakunka-Matata suggested:

```
sudo fdisk -lu
```

Also, open Gparted (partition editor) and take a screenshot of the Gparted window. Alt+PrintScr is the keyboard shortcut. Post the screenshot and then we can see what is what.

---

### Post by weezilla on 2011-07-28
Here is a screenshot of my partitions from within windows. I am about to try the installation, but I'm betting it will hang unless I create partitions from the unallocated space. For some reason, I was able to get into ubuntu. I opened gparted and took screenshots, but it won't let me mount any thumb or external hard drives, and I cannot access the internet even though I have been assigned an IP. The whole thing is acting very fishy.

I am going to reboot and try again to get the screenshots off. I am very happy once ubuntu is installed, but this installer is giving me a lot of trouble :(

[IMG]http://www.weezilla.com/diskmanagement.png[/IMG]

---

### Post by weezilla on 2011-07-28
Here is my "screenshot."

The 112Gb is the unallocated space from windows. Could someone walk me through making the partitions? And is it possible to have my 15gb fat32 partition as well to share files between windows and linux?

Thanks !!

[IMG]http://www.weezilla.com/2011-07-28 22.50.51.jpg[/IMG]

---

### Post by Blasphemist on 2011-07-28
It does look like you have used your last primary partition again with the fat32 partition. I'll point you to a step by step guide that will be perfect for you but, you'll need to delete the fat 32 partition and create an extended partition from it or let the ubuntu installer create that space. The easiest is to just delete the fat32 and let ubuntu do it. Best practice is to do it yourself. You would create an extended partition in all of the unused space (now the fat32 partition). Then in that extended partition create logical partitions for / (root) and swap. You could also create on and have its mount point be /Home. Swap needs to be just bigger than the amount of memory you have. / only needs to be 10-20 GB if you are using a /Home partition. /Home needs to be large enough for all your music, pictures, videos, and settings. This link covers it all. You would have some learning to do but it would be a good thing. Again though, the easiest is to let Ubuntu do all this after you delete the fat32. [http://members.iinet.net.au/~herman546/index.html](http://members.iinet.net.au/~herman546/index.html)

---

### Post by Hakunka-Matata on 2011-07-28
Yes, we can do it.  sda4 is now a FAT32 partition, the post before showed the 112GB as unallocated, you just created the FAT32 partition?, if so no problem.  please respond and we'll go from here if you are ready.  BTW, Ubuntu has no problem reading and writing to ntfs partitions, so I don't really see the need for a FAT32 partition.

Primary partitions on the first hard disc are numbered sda1, sda2, sda3, and sda4.  Logical partitions start with sda5 and continue up from there.

I've included a simple screenshot of this system which has two ubuntu installations on it, sda1 and sda6.  sda1 is a ubuntu 9.10 root, and sda6 is an ubuntu 10.10 OS, and it's being used now as I type, it's got a mount point listed "/" which indicates it is the currently running partition.  All for reference only

---

### Post by oldfred on 2011-07-28
Your windows install was converted to dynamic or SFS partitions.

Posts by oldfred & srs5694
[http://ubuntuforums.org/showthread.php?t=1705481](http://ubuntuforums.org/showthread.php?t=1705481)
SFS converting:
[http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk.html](http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk.html)
Dynamic volume is a Microsoft proprietary format developed together with Veritas (now acquired by Symantec) for logical volumes.
You can use a third-party tool, such as Partition Wizard 4.2. to convert a convert a dynamic disk to a basic disk without having to delete or format them.
The Partition Wizard software for Windows is supposed to be able to convert dynamic disks to regular partitions without data loss, so it may be what you need to get around this problem; however, I've never used it and so I can't be sure it will work.

One user used these two:
MiniTool Partition Wizard Professional Edition 5.2 to convert without loss of data the disk from dynamic disk to a basic disk.
also used Partition Wizard to set an existing partition logical instead of primary
[http://www.partitionwizard.com/convertpartition/convert-to-basic-disk.html](http://www.partitionwizard.com/convertpartition/convert-to-basic-disk.html)
Converted from dynamic with MiniTool, & repaired windows
[http://ubuntuforums.org/showthread.php?t=1779529](http://ubuntuforums.org/showthread.php?t=1779529)

can I mount my WinXP software RAID 0 array in Ubuntu/Kubuntu? dynamic use mdadm
[http://ubuntuforums.org/showthread.php?t=833653&highlight=dynamic+disk](http://ubuntuforums.org/showthread.php?t=833653&highlight=dynamic+disk)

---

### Post by weezilla on 2011-07-28
oldfred, is it necessary/helpful to convert it back from a dynamic disc to a basic disc?

Hakunka-Matata, I'm read to begin whenever you are. I've deleted the FAT32 partition using gparted and am awaiting instructions (Blasphemist, thanks for the links. I'm going to walk through this process with you guys if that's alright?).

---

### Post by Blasphemist on 2011-07-28
oldfred, sorry, I won't miss that again. He did already resize and create that fat32. Does that affect this since he has now deleted it and has free space?

weezilla, let's see what oldfred says if possible before going ahead.

---

### Post by Hakunka-Matata on 2011-07-29
I completely agree, I do not know the significance or implications imposed by a converted Basic Windows disc, into a dynamic disk. That being said, I don' t want to proceed now weezilla, don't want to mess it up.  Oldfred, I'll wait on more of your wise words.

---

### Post by Hakunka-Matata on 2011-07-29
Well, there's a fly in the oinment:  Quite clear discription, discussion on the topic [http://http://ubuntuforums.org/archive/index.php/t-1755070.html. ]("http://http//ubuntuforums.org/archive/index.php/t-1755070.html")

Time for a break, until later, this is a very interesting / albeit unfortunate turn of events, wonder how it will turn out?

---

### Post by Blasphemist on 2011-07-29
It's gettin late and I have to be up in 6 hours. I'll look at this in the morning if for no other reason than to learn.

---

### Post by weezilla on 2011-07-29
Alright Blasphemist, thanks. Hope to hear back something encouraging. I already tried in disc manager to convert it back to a basic disc, but it's not highlighted.

---

### Post by Hakunka-Matata on 2011-07-29
Reverting the disc back to a basic disc is the first step, agreed?  There are several methods listed in the links to accomplish that.  I'll check in tomorrow to see how it's going.  Good Luck.

---

### Post by Quackers on 2011-07-29
Yes "dynamic disks" instead of "simple volumes" means that at some time you have tried to create a 5th primary partition. At this point Windows will normally ask you if you want to proceed. You should always say no to this!
Dynamic disks are fine for Windows, but it means that you will not be able to install any other operating system on there, as the installer won't "see" those dynamic disk type partitions.
As far as I'm aware converting dynamic disks back to simple volumes is a bit hit and miss, at best (unless things have changed lately).
Other users I've seen with this problem have ended up re-installing or recovering their Windows installation.

---

### Post by weezilla on 2011-07-29
I think I've fixed the problem. I used the sfdisk guide on this page (last post). It was a very straight-forward process.

[http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk-10.html](http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk-10.html)

Can I delete the 1mb /dev/sda1 partition that is before my boot record?

---

### Post by Quackers on 2011-07-29
Well that's good to know. Does Windows Disk Management screen report basic or simple volumes now?
Leave the 1MB as a boundary. It's no space at all in real terms.

EDIT - actually, what 1MB partition?

---

### Post by weezilla on 2011-07-29
See my ubuntu gparted screenshot. It is 1mb takng up an entire partition.

---

### Post by Quackers on 2011-07-29
Do you mean the 1MB "unallocated space" entry at the end of the disc?
That's not a partition - that's just empty space - not to be fretted about.

---

### Post by weezilla on 2011-07-29
I'm not concerned about the space; just about it taking up an entire partition. See this recent screenshot. Is this actually a partition?

[IMG]http://www.weezilla.com/gpart edit.jpeg[/IMG]

And yes, Windows now shows the disk and a Basic Disk.

EDIT: Sorry, was trying to skip a step. Uploaded it from my phone.

---

### Post by Quackers on 2011-07-29
Edited

Oh I see!
Yes you can delete that 1MB sda1 partition.
How did that get there?

---

### Post by weezilla on 2011-07-29
There since the beginning. So, I'm just going to make an ext4 partition mounted in "/" and a fat32 partition?

---

### Post by Quackers on 2011-07-29
It was not there in the beginning.
You had a system reserved partition, your Windows partition, a recovery partition and the HP TOOLS partition.
Something has changed, other than the 2 partitions you've deleted.

If you want to create the Ubuntu partitions manually you can do so but I would advise that you make them LOGICAL and not PRIMARY. You can also create a FAT32 LOGICAL partition as well, if you want to.

---

### Post by weezilla on 2011-07-29
Thanks. I was worried because in my screenshot on page two, it has the label "SYSTEM" next to it. I will go ahead and delete it though.

I'll give the install a shot now. Question of curiosity: logical partitions won't take up a primary slot, right? 

Thanks so much for the help, btw. It is very kind of you to take your time to help me.

---

### Post by Quackers on 2011-07-29
If you create logical partitions they will all be enclosed by an extended partition which will be created automatically. This extended partition is a type of primary partition, but partitions within it are not.

Edit
The partition labelled as SYSTEM in the screenshot on page 2 is 199MB not 1MB. Your new sda1 partition is just that - new.

---

### Post by coffeecat on 2011-07-29
> **weezilla said:**
> Thanks. I was worried because in my screenshot on page two, it has the label "SYSTEM" next to it. I will go ahead and delete it though.

Do **not** delete the partition labelled "SYSTEM"! That is your Windows 7 boot partition. I assume you'll be wanting to boot into Windows. :?

---

### Post by weezilla on 2011-07-29
> **Quackers said:**
> 
Edit
The partition labelled as SYSTEM in the screenshot on page 2 is 199MB not 1MB. Your new sda1 partition is just that - new.

The 1MB is labelled SYSTEM. sda2, the 200mb partition, has the flag "boot"?

---

### Post by Quackers on 2011-07-29
Where is it labelled SYSTEM? In what programme?

---

### Post by weezilla on 2011-07-29
In gparted on page two. This doesn't show now, as you can see in my recent screenshot.

---

### Post by Quackers on 2011-07-29
As already stated, I have no idea what that partition is or how it got there.
If you're not sure then DON'T delete it. It's not a problem as long as all future partitions are logical.

---

### Post by weezilla on 2011-07-29
[http://askubuntu.com/questions/26639/installer-doesnt-display-partition-i-want-to-install-to](http://askubuntu.com/questions/26639/installer-doesnt-display-partition-i-want-to-install-to)

I found someone else who had it. They say Windows probably left a 1mb gap when installing. I'll go ahead and delete it. I just got a break so I can actually install linux now. Be back soon. Thanks.

---

### Post by weezilla on 2011-07-29
It's installed and grub is working great. Thanks for all of your help. I will mark it as solved. 

SUMMARY:
I wanted to install linux. In windows, I shrank the OS partition to create 120gb of unallocated space and booted into Ubuntu 11.04 64bit install. I tried to create two partitions (one for file sharing between windows/linux and the other for the linux OS). But HP DV7T laptops come with 4 primary partitions (see below). 

HP Boot Partition (200mb)
HP_Tools Partition
HP Recovery Partition
HP OS partition

I could not install Ubuntu because the four primary partitions had been used already. I did not know this at the time, so I went back into windows and created two partitions out of the unallocated space. In the process of, I accidentally converted my hard drive to a Dynamic Disk (from a basic disk). A dynamic disk is windows specific and will not play well with any other OS (or old MS OS). I booted back into linux to install and got all kinds of weird behavior (like could not mount thumb drives). I deleted the HP_Tools and Recovery partitions, after backing them up. I used the guide in post #96 at [http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk-10.html](http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk-10.html) to convert my drive back to a basic disk (with no problem at all !). I booted into linux and deleted the 1MB partition that my laptop came with (but only linux listed it, not windows). I created a 20gb swap and 100gb logical ext4 partition mounted at "/" and installed linux. I had no problem getting into linux or windows after this, however my windows clock was turned back several hours (although still on the correct minute). I don't know the reason for this, but who cares :)

If anyone has any questions in the future, please email me at gmail.

Thanks for all of your help you guys. God bless you :)

---

### Post by Quackers on 2011-07-29
You're welcome.
Glad you got things sorted out :-)

BTW 20GB for swap is HUGE :-)
My swap partition is just over 2GB and if I didn't use the hibernate facility I would have a much smaller swap.

---

### Post by oldfred on 2011-07-29
Did you select the correct timezone when you installed. 

You can check with System, preferences, system settings, date & time icon.

---

### Post by weezilla on 2011-07-29
The time problem was on my windows system. 

I chose a big swap just in case (I don't really need the space)--I am doing astrophysics simulations for a research project which are very memory intensive. 

[http://mesa.sourceforge.net/](http://mesa.sourceforge.net/)

It's a very impressive software, albeit quite difficult to setup. I spent the first half of the summer choosing parts for our desktop and getting it installed.

---

### Post by Hakunka-Matata on 2011-07-29
Very glad to see you've succeeded in converting your disc back to a basic disc, and that deleting sda1 turned out not to be a problem.  I read a lot about Microsoft's use of 1MiB offsets at beginning of partitions, done to increase performance.  That's a very general description.  This thread taught me a lot, especially concerning basic and dynamic disc's, why they are created and the kinds of problems they cause for people trying to install a second OS.  Many very savvy contributors to the thread, thanks.

---

### Post by n9jfg on 2011-07-31
I am working on a similar problem Dual boot Ubuntu and Windows 7 on a HP Pavillion dv7-6157cl. I have limited use for Win7 only 2 or 3 programs that I can't get to run under wine.

I've read a number of posts on resizing Windows and question the value of resizing for my requirements.  I also have see no value in the HP junk. I have a set of Windows Home Premium disks.

With that being said, my alternative plan is -
Blow a way the HP install and reinstall in a 250 GB partition.
Then do a Ubuntu install of 10.10

Does anyone know of specific caveats?

Any other comments?

Thanks

John n9jfg

---

### Post by oldfred on 2011-07-31
@n9jfg
I would still suggest you make the recovery DVDs and a windows repair CD. That way if you have second thoughts or ever want to sell it and the buyer wants the original Windows you have a way.


Some examples of installs and issues with 10.10:
Issues on dual boot in same drive:
[http://ubuntuforums.org/showthread.php?t=1622388](http://ubuntuforums.org/showthread.php?t=1622388)
From kansasnoob:
[http://ubuntuforums.org/showpost.php?p=10145206&postcount=15](http://ubuntuforums.org/showpost.php?p=10145206&postcount=15)
Trust me here! If you choose either "Use entire partition" or "Use entire disc" you are not likely to end up with "Alongside" anything! You will most likely lose the OS and any data contained therein!

Install 11.04
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)
Ubuntu Install steps - then choose guide, close to what you want.
[http://members.iinet.net/~herman546/index.html](http://members.iinet.net/~herman546/index.html)
Installs with good screenshots/examples:
[http://members.iinet.net.au/~herman546/p22.html](http://members.iinet.net.au/~herman546/p22.html)

---

### Post by Blasphemist on 2011-07-31
I could voice my opinions that mainly boil down to I'd leave windows in place since you have a few programs you need to keep using. I did shrink windows 7 by first defragging a hundred times then trying the windows disc utilities to shrink it's partition. Your success with this may be limited in that you may not get a lot of free space. On the other hand you may have good success in the shrink.

Once you have that done, you should get rid of any un-needed partions. If you post a screen shot of your partitions you will get suggestions on what you can get rid of. You can make windows recovery discs and if there is a utility partition you can likely download a better set now. 

At this point you will have free space and you should then use this site to guide you implementing dual boot. It is a very good site with good explanation and examples including screen shots. [http://members.iinet.net.au/~herman546/index.html](http://members.iinet.net.au/~herman546/index.html)

When I first implemented ubuntu and dual boot, I let the install do it without me doing the partitioning. I've since shrunk windows more and made a bunch of new partitions for distros other than my main ubuntu partition. You may or may not feel comfortable doing partitioning yourself but it is best practice.

---

