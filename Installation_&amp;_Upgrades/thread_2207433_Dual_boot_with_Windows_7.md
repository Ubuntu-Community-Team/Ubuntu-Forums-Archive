---
title: "Dual boot with Windows 7"
date: 2014-02-22
forum: Installation &amp; Upgrades
---

### Post by Faraz_Bukhari on 2014-02-22
Hi everyone. I am on Windows 7 right now and I have created a partition on my 550 GB hard drive so I can install Ubuntu on it. The partition size is 175 GB. I have put Ubuntu on a USB drive using UNetBootin. I successfully am able to boot into Ubuntu but when I click on the install icon and go through the steps until I get to the step where it asks me HOW I want to use Ubuntu, that is where I have a problem. I click on the option that says to install it side by side with Windows 7. I click on it and for a moment it loads and than a black screen shows up for a maybe a second (if even that) and than it brings me back to the UNetBootin screen where I have to select whether I would like to try or install ubuntu and other options as well. So I whether I select try or install, it brings to me the same screen - the original desktop still running off of the USB drive. PLEASE HELP! I really want to use Linux as I have heard it is very customizable and I am a big fan of Android! PLEASE HELP ME!

---

### Post by Topsiho on 2014-02-23
I am not sure, but maybe (I never install alongside Windows) Ubuntu needs to install into unallocated space in this case. So you must make the 175 GB partition unallocated space for the install to run correctly. Do this in Windows itself, and after doing so first boot into Windows before proceeding. To let Windows adjust to the new situation.
You don't tell what version of Ubuntu you try to install, and how old your computer is. Possibly the hardware in your computer is not (yet) recognized by your Ubuntu.

Second: Ubuntu is NOT Android. Ubuntu is very safe and Android is (sorry to say this, ah, I 'll say it neatly) a purposefully borked version of Linux, with a lot of closed software on top of it, from Google, the manufacturer, and probably the provider, all sniffing at your private life.

Topsiho

---

### Post by Impavidus on 2014-02-23
Windows cannot create the kind of partition Ubuntu needs. Ubuntu has difficulty shrinking Windows partitions (Vista and up, it had no problem with WinXP partitions), so the best approach is to use Windows tools to create unallocated disk space.

---

### Post by Topsiho on 2014-02-23
I do agree. As far as I know Windows 7 has a tool equivalent to Partition Magic (a (once existent?) Windows partition program) and GParted. Use that Windows tool to create some unallocated space, and next let Ubuntu install do its work. Automatically, or do a custom install:
 a partition for root ( / ), of let's say 5 to 20 GB, depending on size of space (175 GB is much, depending on what is needed), file system ext4, then swap space (rule of thumb is 2 times ram), and the rest of the space for the /home partition, file system ext4.

If you let Ubuntu install do it automatically you get a / partition, ext4, possibly a primary partition, and a swap partition, probably a logical partition.

To be sure: The maximum number of primary partitions you can have on a disk is 4, if you need more than that you must sacrifice one primary partition to create an extended partition, in which you can create any number of logical partitions.

This may be the cause of Faraz_Bukhari's problem by the way ... that all 4 primary partitions are already used.

Topsiho

---

### Post by The Cog on 2014-02-23
As the other say, Windows cannot create the kind of partitions that Ubuntu needs. 
Also, the Ubuntu installer will see the partition you created and regard it as allocated/used space - after all, there is a partition there. 
Your best bet is to delete the partition using the windows disk tools, leaving the space truly unallocated. Then let the Ubuntu installer install into the unallocated space.

Back up your windows data first, just to be on the safe side.

---

### Post by Faraz_Bukhari on 2014-02-23
> **The Cog said:**
> As the other say, Windows cannot create the kind of partitions that Ubuntu needs. 
Also, the Ubuntu installer will see the partition you created and regard it as allocated/used space - after all, there is a partition there. 
Your best bet is to delete the partition using the windows disk tools, leaving the space truly unallocated. Then let the Ubuntu installer install into the unallocated space.

Back up your windows data first, just to be on the safe side.

I have attached the view of my disk management screen. How do I go about erasing the 175 GB of allocated space and making extra allocated space on my hard disk as you say.

---

### Post by Faraz_Bukhari on 2014-02-23
Can somebody please help me with the problem I am having?  I am on Windows 7 right now and I have created a partition on my 550 GB hard drive so I can install Ubuntu on it. The partition size is 175 GB. I have put Ubuntu on a USB drive using UNetBootin. I successfully am able to boot into Ubuntu but when I click on the install icon and go through the steps until I get to the step where it asks me HOW I want to use Ubuntu, that is where I have a problem. I click on the option that says to install it side by side with Windows 7. I click on it and for a moment it loads and than a black screen shows up for a maybe a second (if even that) and than it brings me back to the UNetBootin screen where I have to select whether I would like to try or install ubuntu and other options as well. So I whether I select try or install, it brings to me the same screen - the original desktop still running off of the USB drive. PLEASE HELP! I really want to use Linux as I have heard it is very customizable and I am a big fan of Android! PLEASE HELP ME! 

I have attached the view of my disk management screen on Windows.

---

### Post by jp734 on 2014-02-23
You were able to partition your hard drive but you did not format it. It still says unallocated and I think that's the reason why it won't let you go to the next step to select the 175GB to use for installation.

---

### Post by dragonfly41 on 2014-02-23
I've read the other thread you started in same topic ..

[http://ubuntuforums.org/showthread.php?t=2207292](http://ubuntuforums.org/showthread.php?t=2207292)

As I understand you have a 175GB unallocated space in your drive and you want to install Ubuntu.

I really can't remember if the Ubuntu installer installs into unallocated space. 
As jp744 writes above it may be that at the "prepare disk space" window the installer requires a pre-formatted linux partition instead of installing into unallocated space.

However Cog in the other thread says "Then let the Ubuntu installer install into the unallocated space".

So I'm not sure about that. But this tutorial will help you ...

[https://help.ubuntu.com/community/Installation/FromUSBStickQuick](https://help.ubuntu.com/community/Installation/FromUSBStickQuick)

I assume that you want to install "side by side" i.e. so that you dual boot between windows 7 and ubuntu. However as pointed out by Topsigo you have hit the four primary partitions limit dictated by Windows and 

> 
To be sure: The maximum number of primary partitions you can have on a disk is 4, if you need more than that you must sacrifice one primary partition to create an extended partition, in which you can create any number of logical partitions.

This may be the cause of Faraz_Bukhari's problem by the way ... that all 4 primary partitions are already used.


So what are your options?

The easiest would be to buy an external drive (bootable) and install Ubuntu into that drive, preserving your Windows 7 unchanged.

Another (more risky) option would be to either delete or backup your NTFS partitions 
D: Recovery
and 
E: HP_Tools
and delete these partitions to give you 175GB + 15.8 GB + 3.97 GB of unallocated space to play with.

But do check the effect of sacrificing these partitions. Your Windows recovery options would be lost.

Now in this 194.77 GB unallocated space (from above exercise) you can use GParted Partition Editor (in your bootable USB Ubuntu > System Tools -> Administration) to create a** logical** (not primary) partition.

You might end up with partitions
/dev/sda1 System NTFS 199 MB
/dev/sda2 C: NTFS 401.21 BG
/dev/sda3 logical container

 
And within the logical container you will need to create new **logical partitions** (there is no limit to the number of logical partitions).

So you could create ...

one logical partition for Ubuntu root "/" .. type Ext4
one logical partition for Ubuntu home "/home" .. type Ext4
one logical partition for Ubuntu swap .. type Swap *(note: later corrected from "Ext4" to type "Swap")*

and you could (optionally) create two logical NTFS type partitions to bring back your cloned Recovery and HP_Tools .. or leave them where you backed them up.

This would be the final structure in GParted.

/dev/sda1 System NTFS 199 MB
/dev/sda2 C: NTFS 401.21 BG
/dev/sda3
.../dev/sda4 Ext4 Ubuntu root .. mount "/"
.../dev/sda5 Ext4 Ubuntu home .. mount "/home"
.../dev/sda6 Swap Ubuntu swap *(note: later corrected from "Ext4" to type "Swap")*
.../dev/sda7 NTFS Recovery
.../dev/sda8 NTFS HP_Tools

Then carefully take note of the /dev/sda4 and /dev/sda5 and /dev/sda6 partition label to be used at the next stage where the installer "prepares disk space".

And I would use the manual option ..
"Specify partitions manually (advanced)". 

Be absolutely sure that you select the correct partitions otherwise you could overwrite Window 7 in /dev/sda1 and /dev/sda2.

Search this forum for more advice on "dual boot" installation and splitting up Ubuntu onto root, home, swap partitions. Or you could just install into one logical partition.

Another option is to just run Ubuntu from an external bootable USB hard drive.  

And yet another option is to forget the above and expand Windows 7 /dev/sda2 to take up the 175 GB unallocated space and then install VirtualBox into Windows.   Then you can install Ubuntu into VirtualBox

Sometimes that is a lot easier than dual booting.

---

### Post by mörgæs on 2014-02-23
Please stop multiposting.
Threads merged.

---

### Post by Faraz_Bukhari on 2014-02-23
Hi everyone. I found out the problem I was having when installing Ubuntu alongside Windows 7 on my machine. Can somebody help me solve the problem. Ok so the problem was that I could not install Ubuntu due to my hard drive already having 4 partitions in it. So I found out that Windows does not allow more than 4 partitions or something like that. I have made 175GB of free space on my machine so I can use it for Ubuntu but when I go to install Ubuntu, it lists the allocated space on my hard disk as unusable space. I am trying to install Ubuntu 12.04. I have attached the view of my disk management screen. Can somebody help me with my problem please. I really want Ubuntu!

[ATTACH=CONFIG]250630[/ATTACH]

---

### Post by westie457 on 2014-02-23
Hi Faraz_Bukhari

First things first.
Make a back-up of the 'Recovery' partition. Do this in Windows.
Next make a Windows recovery CD.
Now move your personal files from Windows to CD\DVD or external hard drive
These are important just in case anything goes wrong.

After you have done the above and you are still booted into Windows go to the MMC Console and delete the 'Recovery' partition.

IT is vital that you leave this space **unformatted**

Now boot into the LiveDVD\USB and go ahead with your installation.

Remember to go through the list in order.

Any problems\issues\questions post back here before it gets out of hand.

Good luck.

---

### Post by Faraz_Bukhari on 2014-02-23
Ok can you help me step by step please. So I have decided that I would like to dual boot on the same hard drive. First of all I want to back up the hp tools and the recovery partitions on my hard drive. Can I back them up to a service such as google drive or drop box or something like that. I do not have an external hard drive or anything like that to back up too. I just use cloud storage.

---

### Post by Faraz_Bukhari on 2014-02-23
[COLOR=#000000] I want to back up the hp tools and the recovery partitions on my hard drive. Can I back them up to a service such as google drive or drop box or something like that? I do not have an external hard drive or anything like that to back up too. I just use cloud storage now. I have 15 GB of free cloud storage to work with.I do not have at is fine if everything gets deleted. I do not have a dvd or hard drive that is why I was wondering if I could just back it up to cloud storage?[/COLOR]

---

### Post by westie457 on 2014-02-23
By all means put your personal files into cloud storage.

To the best of my knowledge the program to back-up the recovery partition in Windows 7 will only allow it to go to DVD, it might work from a USB drive though I have never tried this. Also I do not know whether HP computers allow a 'Network Boot' to download over a network. Another thing against storing the recovery in the cloud is this partition is basically one file approximately 16GB in size. Most cloud services have a maximum upload size per file that at most is 2GB and will take a very long time to upload.

IMHO the recovery partition really must go to DVD (allow 5 dvds) or one 16GB usb drive if your computer allows this and the Windows recovery CD must be a CD or another USB drive. I do not have a HP computer so do not know what the HP-Tools will allow.

Maybe someone who knows more about this will find this thread and advise accordingly.

---

### Post by sammiev on 2014-02-23
Your disk management screen shows a DVD. I would suggest you backup what was suggested above so you can return to where you are if things go wrong.

---

### Post by SuperFreak on 2014-02-23
This was my solution [http://ubuntuforums.org/showthread.php?t=2191419&highlight=primary+partitions]("http://ubuntuforums.org/showthread.php?t=2191419&highlight=primary+partitions")  POST #12

---

### Post by nosmadar on 2014-02-23
Just an FYI for any future readers who see this post. I created a Dual boot configuration, starting with Win 7 and adding Ubuntu, by basically just letting Ubuntu handle everything.  As in I just put the Ubuntu install disk in the CD drive, rebooted my PC so that it would boot from the CD drive, and let the Ubuntu (12.04) install disk take care of everything.  And it worked fine.  The only catch here was that I was willing to have Ubuntu be the "master" boot partition.   The complicated part came later when I eventually was so happy with Ubuntu that I wanted to shrink the NTFS (Win 7) partition and allocate more space to Ubuntu.  Then I had to create an stand alone boot disc with Gparted on it. (I think it used a subset of Debian to do this).  But even that worked out Ok.

---

### Post by The Cog on 2014-02-24
I think I can see a problem here. The windows disk manager shows 4 primary partitions in use. If it is using an MSDOS type partition table rather than EFI, then you cannot have more than 4 primary partitions, so you cannot make use of the unallocated space.

The normal thing to do (with an MSDOS partition table) would be to use one of the four primary partitions as an "extended" partition that acts as a container for any number of "logical" partitions. But this might be difficult in your case as you don't have a spare partition that you can use as an extended partition. 

That said, I'm not clear whether your partition table is MSDOS or EFI, and I know the windows disk utility sometimes lies about what's really there, to to be sure can you please run the live CD, open a terminal window and enter the command
```
sudo parted -l
``` and post the output here. Then we will know what we are really dealing with.

---

### Post by Impavidus on 2014-02-24
I think that to be useful, the Windows recovery partition has to be on the hard drive, and probably as a primary partition. So I wouldn't touch it. The HP_TOOLS partition however is not incredibly useful. So, to be sure, you can create a backup of it on DVD or wherever you want (it's only 4GB) and then delete it using your Windows partitioning tool. Now you can run the Ubuntu installer from the live disk. If you choose to install side by side, it will automatically create an extended partition in your unallocated space and put the Ubuntu partitions in there, automatically creating decently sized partitions. This will leave 4GB useless unallocated space at the end of the disk, but that won't matter much on a disk of this size.

Instead of doing the side by side installation you can also do it manually. This will allow you to create a separate /home partition (not necessary, but often recommended) and/or a shared data partition (type NTFS), which is useful if you want to share data between Windows and Linux. Allowing Ubuntu to write directly to the C partition is a recipe for disaster.

BTW, the swap partition will be type swap, not ext4.

---

### Post by Mark Phelps on 2014-02-24
Since you already have four partitions, that is the maximum allowed. Simply removing HP_TOOLS is not the solution -- as it is too small to be of any use.

So first, copy all the files and folders inside the HP_TOOLS partition into your Win7 OS partition.  

Second, open up the Win 7 Disk Management tool.  NOW, you can remove the HP_TOOLS partition.

Third, shrink the Win7 OS partition to make room on the drive. Win7 is very finicky about its OS partition being messed with from "outside" with other tools -- like GParted. While it may be OK, it's more likely to result in filesystem corruption, which will then render Win7 unbootable.

Fourth, you will need a way, in the future, to restore Win7 to its present state -- and you can do that without using the Recovery partition.  Download and install the free version of Macrium Reflect.  Hook up an external drive, and use MR to image off the Win7 OS and its boot partition to that drive.  Then, use the MR option to create and burn a Linux Boot CD.

Now, using that CD, you have the ability to restore your current Win7 setup from that backup. 

Fifth, you can now go back into the Win7 Disk Management tool and remove the Recovery partition. Do not format the free space, leave it as is.

Finally, BEFORE you install Ubuntu, use the Win7 Backup feature to create and burn a Win7 Repair CD.  You might need this later if the dual-boot install corrupts the Win7 boot loader.

When you then install Ubuntu, use the "Something Else" option to allow Manual Partitioning.

---

### Post by Faraz_Bukhari on 2014-02-24
> **The Cog said:**
> I think I can see a problem here. The windows disk manager shows 4 primary partitions in use. If it is using an MSDOS type partition table rather than EFI, then you cannot have more than 4 primary partitions, so you cannot make use of the unallocated space.

The normal thing to do (with an MSDOS partition table) would be to use one of the four primary partitions as an "extended" partition that acts as a container for any number of "logical" partitions. But this might be difficult in your case as you don't have a spare partition that you can use as an extended partition. 

That said, I'm not clear whether your partition table is MSDOS or EFI, and I know the windows disk utility sometimes lies about what's really there, to to be sure can you please run the live CD, open a terminal window and enter the command
```
sudo parted -l
``` and post the output here. Then we will know what we are really dealing with.

> **Impavidus said:**
> I think that to be useful, the Windows recovery partition has to be on the hard drive, and probably as a primary partition. So I wouldn't touch it. The HP_TOOLS partition however is not incredibly useful. So, to be sure, you can create a backup of it on DVD or wherever you want (it's only 4GB) and then delete it using your Windows partitioning tool. Now you can run the Ubuntu installer from the live disk. If you choose to install side by side, it will automatically create an extended partition in your unallocated space and put the Ubuntu partitions in there, automatically creating decently sized partitions. This will leave 4GB useless unallocated space at the end of the disk, but that won't matter much on a disk of this size.

Instead of doing the side by side installation you can also do it manually. This will allow you to create a separate /home partition (not necessary, but often recommended) and/or a shared data partition (type NTFS), which is useful if you want to share data between Windows and Linux. Allowing Ubuntu to write directly to the C partition is a recipe for disaster.

BTW, the swap partition will be type swap, not ext4.

Ok so I was thinking. Since I am only allowed to have 4 partitions on my hard disk, how about I back up and delete the HP_tools partition

[ATTACH=CONFIG]250652[/ATTACH]

So if I delete the HP_tools partition on my hard drive, I can use the unallocated space for Ubuntu. And then when I go to install, I can just select the option to install side by side with Windows 7 automatically and it will make my partitions for me. Right?

---

### Post by oldfred on 2014-02-24
Still always best to use Windows to shrink the Windows partition and reboot into Windows before installing Ubuntu. Also have a Windows repairCd or flash drive and make a full backup of Windows.

And then you should be able to install into the unallocated space.

       My laptop already has 4 primary partitions: how can I install Ubuntu?
[http://askubuntu.com/questions/149821/my-laptop-already-has-4-primary-partitions-how-can-i-install-ubuntu](http://askubuntu.com/questions/149821/my-laptop-already-has-4-primary-partitions-how-can-i-install-ubuntu)
Good advice on how to handle all four primary partitions used. - srs5694
[http://ubuntuforums.org/showthread.php?t=1686440](http://ubuntuforums.org/showthread.php?t=1686440)
Be sure to create recovery DVD(s) first. And a Windows repair CD.
HP tools partition discussion - similar for other vendor utility partitions:
[http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360](http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360)
For a complete blow-by-blow on dealing with HP's four partitions, see Full Circle Magazine, issue 41, page 36. - gordintoronto
[http://fullcirclemagazine.org/](http://fullcirclemagazine.org/)

---

### Post by Faraz_Bukhari on 2014-02-24
1. I copied all the folders to my C drive. I made a new folder in my C drive and named it "HP_TOOLS".
2. I removed the HP_TOOLS partition from my disk management utility. 
Now my disk utility screen looks like this:

[ATTACH=CONFIG]250653[/ATTACH]

3. I want  at least 175 GB for Ubuntu so can you please tell me how much to shrink it?

---

### Post by sammiev on 2014-02-24
> **Faraz_Bukhari said:**
> 1. I copied all the folders to my C drive. I made a new folder in my C drive and named it "HP_TOOLS".
2. I removed the HP_TOOLS partition from my disk management utility. 
Now my disk utility screen looks like this:

[ATTACH=CONFIG]250653[/ATTACH]

3. I want  at least 175 GB for Ubuntu so can you please tell me how much to shrink it?

You are not reading what people are telling you. Make a working backup of your HD and or a full working copy of your OS.

---

### Post by Faraz_Bukhari on 2014-02-24
I know that but Mark Phelps said that I have to shrink the drive that Windows 7 is installed on. How much do I shrink it by?!?

---

### Post by Faraz_Bukhari on 2014-02-24
> **Mark Phelps said:**
> 
Third, shrink the Win7 OS partition to make room on the drive. Win7 is very finicky about its OS partition being messed with from "outside" with other tools -- like GParted. While it may be OK, it's more likely to result in filesystem corruption, which will then render Win7 unbootable.


Why should I shrink the partition. Look at my disk utility screen. I have 180GB of unallocated space. That is more than enough for what I want with Ubuntu.

---

### Post by oldfred on 2014-02-25
You do not need to shrink Windows any more unless you want to also create a separate NTFS shared data partition. Often best to have another partition for shared data and configure Ubuntu as read only on Windows system partition. Avoids accidents as the Linux NTFS driver exposes all the normally hidden Windows files & folders. 

Also make sure Windows is not hibernated.

If you have rebooted Windows so chkdsk has run, then the auto install option should show install side by side as an install option. Default install is / (root) and swap. 
We do often suggest a separate /home or data partitions (or both). You cannot create the NTFS shared data partition during install, but can create partitions in advance with gparted if desired. But to create more than

---

### Post by Faraz_Bukhari on 2014-02-25
> **oldfred said:**
> You do not need to shrink Windows any more unless you want to also create a separate NTFS shared data partition. Often best to have another partition for shared data and configure Ubuntu as read only on Windows system partition. Avoids accidents as the Linux NTFS driver exposes all the normally hidden Windows files & folders. 

Also make sure Windows is not hibernated.

If you have rebooted Windows so chkdsk has run, then the auto install option should show install side by side as an install option. Default install is / (root) and swap. 
We do often suggest a separate /home or data partitions (or both). You cannot create the NTFS shared data partition during install, but can create partitions in advance with gparted if desired. But to create more than

Ok since I do not have a spare disc or USB drive at hand, I am going to just delete the recovery partition because I found a website online that provides me with the recovery software that I can just burn to a disc. I will just do that than. Ok so now that I deleted the recovery partition on my hard drive, I am ready to boot into Ubuntu. Now Mark Phelps said to install it through the manual procedure.  If I do that, than what all do I change and stuff. Can you please tell me. Thank You.

---

### Post by oldfred on 2014-02-25
Still best to backup Windows. 
       The vendor recovery DVDs are just an image of your drive as purchased. If you have housecleaned a lot of cruft normally included, run many updates with many reboots, and added software you may want a full back up.
Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710](http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

A variety of install procedures. Only minor difference in screen shots for older versions.
      
 [https://sites.google.com/site/easylinuxtipsproject/first](https://sites.google.com/site/easylinuxtipsproject/first)
Install with screen shots, auto install option
[http://howtoubuntu.org/how-to-install-ubuntu-13-04-raring-ringtail#.UfFD-uHAMfT](http://howtoubuntu.org/how-to-install-ubuntu-13-04-raring-ringtail#.UfFD-uHAMfT)
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)
Install options, Do not use erase entire drive unless that is really what you want. That is entire hard drive not just Windows c: "drive".
[http://www.ubuntu.com/download/help/install-desktop-long-term-support](http://www.ubuntu.com/download/help/install-desktop-long-term-support)

 [https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)
[http://askubuntu.com/questions/6328/how-do-i-install-ubuntu](http://askubuntu.com/questions/6328/how-do-i-install-ubuntu)

---

### Post by Faraz_Bukhari on 2014-02-25
> **oldfred said:**
> Still best to backup Windows. 
       The vendor recovery DVDs are just an image of your drive as purchased. If you have housecleaned a lot of cruft normally included, run many updates with many reboots, and added software you may want a full back up.
Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710](http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

A variety of install procedures. Only minor difference in screen shots for older versions.
      
 [https://sites.google.com/site/easylinuxtipsproject/first](https://sites.google.com/site/easylinuxtipsproject/first)
Install with screen shots, auto install option
[http://howtoubuntu.org/how-to-install-ubuntu-13-04-raring-ringtail#.UfFD-uHAMfT](http://howtoubuntu.org/how-to-install-ubuntu-13-04-raring-ringtail#.UfFD-uHAMfT)
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)
Install options, Do not use erase entire drive unless that is really what you want. That is entire hard drive not just Windows c: "drive".
[http://www.ubuntu.com/download/help/install-desktop-long-term-support](http://www.ubuntu.com/download/help/install-desktop-long-term-support)

 [https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)
[http://askubuntu.com/questions/6328/how-do-i-install-ubuntu](http://askubuntu.com/questions/6328/how-do-i-install-ubuntu)
Ok so if I want just a normal install without the extra partition to have a shared folder or anything, can I just do a auto install thing. So all I want are the necessary partitions and that is all. I want at least 150GB for Ubuntu. With the Swap partitions taking up space and the other partitions that the auto install makes, will I be able to have 150GB left just for files and programs that I use on Ubuntu?!?!?

---

### Post by oldfred on 2014-02-25
You can have one large partition as / (root). Then your /home is inside that partition and you can easily use the entire size for programs or data.  For a new user that is all that is required.

Only if familiar with partitions and what a separate partition for data then you have to do manual install or something else. But then you have to manually create each partition, choose format like ext4, choose mount like / or /home or swap. Location for boot loader like default sda drive.

---

### Post by Faraz_Bukhari on 2014-02-25
> **oldfred said:**
> You can have one large partition as / (root). Then your /home is inside that partition and you can easily use the entire size for programs or data.  For a new user that is all that is required.

Only if familiar with partitions and what a separate partition for data then you have to do manual install or something else. But then you have to manually create each partition, choose format like ext4, choose mount like / or /home or swap. Location for boot loader like default sda drive.

so basically I'll be fine with auto install?

Sorry, I just want to make any mistakes.

---

### Post by oldfred on 2014-02-25
As long as the auto install sees Windows and offers side by side install. If only option is overwrite entire drive then you have to partition in advance with gparted and then still use Something Else to choose partitions.

---

