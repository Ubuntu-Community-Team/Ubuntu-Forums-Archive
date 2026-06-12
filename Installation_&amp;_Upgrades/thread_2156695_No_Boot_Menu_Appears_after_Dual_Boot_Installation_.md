---
title: "No Boot Menu Appears after Dual Boot Installation with Windows 7 Pro"
date: 2013-06-22
forum: Installation &amp; Upgrades
---

### Post by omer7 on 2013-06-22
Hello everyone,

I've a Windows 7 Professional laptop, and want to install Ubuntu 13.04 alongside Windows 7. But facing some issue. Here it is:

My laptop came with Windows 7 Pro (64-bit), and I've made 6 partitions (or logical drives, whatever it is called) in it. Recently I installed Windows 8 in my laptop (Dual boot with Win 7), but then I wanted to try Ubuntu, so I formatted Drive D: (in which Win 8 was installed) and through "msconfig", I removed Win 8 from boot option, so that my PC could directly boot into Win 7 (which it is doing perfectly).

Now when I want to install Ubuntu, it says, "Install Ubuntu alongside Windows 8" (and some other options).

Why it is detecting Win 8 (though I don't have it in my laptop anymore). It doesn't detect Win 7 in my laptop.

Anyway I went ahead and selected the option "Install ubuntu alongside Windows 8".
-Formatted one drive with ext4 and then there was some option where I selected "\" (I was not sure whether to select "\" or "\boot") :(

But after installation my PC directly boots to Win 7, no boot menu appears when I start my PC with options of Ubuntu and/or Win 7.

I searched online, couldn't really find any solution, but tried bootrec \fixmbr, bootrec \fixboot etc commands, but still ubuntu detects windows 8 in my laptop.

Can anyone please guide me how can I make ubuntu detect Windows 7 in my laptop and after installation it gives me boot menu options?

And one more thing, what should I select when formatting/selecting partition for ubuntu installation?
-ext4?
-\ or \boot or something else?

Thanks and sorry for such a long text :)

---

### Post by debodas on 2013-06-22
What it looks like to me, is that the Ubuntu installer failed to install grub.

In my view, the easiest way to fix this problem is to reinstall Ubuntu (I'm assuming you haven't been able to boot into it, so no programs/docs are there?

When installing again, select the 'Something else' installation option. Ext4 is what your / partition should be - do you have a /home? If so, make that Ext4 as well. Install GRUB to /dev/sda, this will give you the option to boot into Windows or Ubuntu when you boot up.

edit - actually, before you do that, can you open up a partition manager, and take a screenshot of your current partition table and post it here? Could be something else going on.

---

### Post by omer7 on 2013-06-22
> **debodas said:**
> What it looks like to me, is that the Ubuntu installer failed to install grub.

In my view, the easiest way to fix this problem is to reinstall Ubuntu (I'm assuming you haven't been able to boot into it, so no programs/docs are there?

When installing again, select the 'Something else' installation option. Ext4 is what your / partition should be - do you have a /home? If so, make that Ext4 as well. Install GRUB to /dev/sda, this will give you the option to boot into Windows or Ubuntu when you boot up.

edit - actually, before you do that, can you open up a partition manager, and take a screenshot of your current partition table and post it here? Could be something else going on.

Thank you very much for your response. Attached is the screen shot of my drive's partitions.

And yeah I've no issue in re installing Ubuntu. I have actually removed Ubuntu (by formatting the drives in which Ubuntu was installed). But when I try to re install it, it again detects Windows 8 (though I don't have windows 8 in my system anymore).

And what is /home btw :(. I'm new to Ubuntu, so don't know much about it. And when I install Ubuntu, I don't really find anything like GRUB :S

---

### Post by debodas on 2013-06-22
If you just have a / partition, everything goes there.

If you have / and /home partitions:
Your distro, and all programs you install, go to /
Your files go to /home

This makes for easy re installation of your distro without deleting all your files.

With regard to your partition table:
C is where Windows 7 is.
G is where you want Ubuntu to be installed.
D is empty - what do you want to use it for?
I presume E and F are part of your Windows 7 setup?

---

### Post by omer7 on 2013-06-22
> **debodas said:**
> If you just have a / partition, everything goes there.

If you have / and /home partitions:
Your distro, and all programs you install, go to /
Your files go to /home

This makes for easy re installation of your distro without deleting all your files.

With regard to your partition table:
C is where Windows 7 is.
G is where you want Ubuntu to be installed.
D is empty - what do you want to use it for?
I presume E and F are part of your Windows 7 setup?

Thanks for the response.

Yeah C is Windows 7 drive
E and F are being used for documents/softwares etc. and songs respectively
D and G are free (I can use both these for ubuntu) (D and G were actually one drive, but I split them into two through partition software)

I want to install everything in one drive with "/".

But again the problem is if I install ubuntu, it first of all (during installation) won't detect Windows 7, but would detect windows 8 (which is no more in my system), secondly even if I install it by selecting the option "Install ubuntu alongside windows 8", it won't give me boot menu option, and would directly boot into windows 7. :(

---

### Post by debodas on 2013-06-22
Sure you want to install it on /? My advice would be / and /home.

If you do want to install everything on /, I would combine D and G. Format is whatever you like.

Then, when installing Ubuntu, select the 'Something else' installation option.  Now format the drive you're going to install Ubuntu on as Ext4, and give it the / mount point.

There will be a option for Grub - Install it to /dev/sda. This should mean you will have the choice of Ubuntu and Windows 7 upon boot.

Last question - have you thought about a swap partition? How much ram does your system have?

---

### Post by omer7 on 2013-06-22
> **debodas said:**
> Sure you want to install it on /? My advice would be / and /home.

If you do want to install everything on /, I would combine D and G. Format is whatever you like.

Then, when installing Ubuntu, select the 'Something else' installation option.  Now format the drive you're going to install Ubuntu on as Ext4, and give it the / mount point.

There will be a option for Grub - Install it to /dev/sda. This should mean you will have the choice of Ubuntu and Windows 7 upon boot.

Last question - have you thought about a swap partition? How much ram does your system have?

Thanks again for ur reply.

Yeah  i ll chk for / and /home option, if i dont understand it i ll combine D and G which wud b easier for me.

My system has 4gig RAM which wud b enough i guess. If not let me know i ll give some partition to swap.

And i remember last time i dint give any partition to use as swap bt ubuntu setup automatically created a swap partition.

And in /dev/sda i think windows 7 boot info wud b installed? Right? So will it b safe to install grub in that?

---

### Post by debodas on 2013-06-22
/dev/sda is where your Master Boot Record is. Perfectly safe to install grub to that. 

4gbs *should *be enough to live without swap, but I'd still make a 4gb swap partition. If I were you, this would be what I'd do:
Shrink G by 4gb 
Make a new, 4gb partition

Go to install, select the Something Else option
Format G as Ext4, give it a mount point of /
Format D as Ext4, give it a mount point of /home
Format the 4gb partition you just made as swap
Install Grub to /dev/sda

You can do all of that from the Ubuntu installer, again, use the something else option.

---

### Post by oldfred on 2013-06-22
Ubuntu will see Windows 8 as you still have the Windows 8 boot files in your Windows 7. A second install of Windows moves all its boot files to the first install and takes over. So all the Windows 7 boot files were in effect replaced with Windows 8. Removing the Windows 8 install does not change the boot files back unless you do a Windows repair from a Windows repairCD.

 [https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)

 
       For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home if allocating over 30GB.:

Ubuntu partitions - smaller root only where hard drive space is limited.
If total space less than about 30GB just use / not separate /home or standard install.
1. 10-25 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext4(or ext3)
3. 2 GB Mountpoint swap logical

   Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.

---

### Post by omer7 on 2013-06-23
> **debodas said:**
> /dev/sda is where your Master Boot Record is. Perfectly safe to install grub to that. 

4gbs *should *be enough to live without swap, but I'd still make a 4gb swap partition. If I were you, this would be what I'd do:
Shrink G by 4gb 
Make a new, 4gb partition

Go to install, select the Something Else option
Format G as Ext4, give it a mount point of /
Format D as Ext4, give it a mount point of /home
Format the 4gb partition you just made as swap
Install Grub to /dev/sda

You can do all of that from the Ubuntu installer, again, use the something else option.

Thanks a lot for your help. Much appreciated. :)

And sorry for replying late, I went to sleep and woke up quite late (coz of weekend).

I'll try the way you've mentioned it here and will let you know how it goes :)

Thanks again.

---

### Post by omer7 on 2013-06-23
> **oldfred said:**
> Ubuntu will see Windows 8 as you still have the Windows 8 boot files in your Windows 7. A second install of Windows moves all its boot files to the first install and takes over. So all the Windows 7 boot files were in effect replaced with Windows 8. Removing the Windows 8 install does not change the boot files back unless you do a Windows repair from a Windows repairCD.

 [https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)

 
       For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home if allocating over 30GB.:

Ubuntu partitions - smaller root only where hard drive space is limited.
If total space less than about 30GB just use / not separate /home or standard install.
1. 10-25 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext4(or ext3)
3. 2 GB Mountpoint swap logical

   Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.

Thank you very much for that. :)

Yeah you're right, I installed Windows 8 recently, so that's why ubuntu is still seeing it. I tried some commands like fixMbr, fixBoot etc. but that didn't help either. I think like you said, I would have to repair windows, but instead of that I'll try the other options as mentioned by a member in above post and lets see how it goes.

Will let you know :)

---

### Post by omer7 on 2013-06-23
> **debodas said:**
> /dev/sda is where your Master Boot Record is. Perfectly safe to install grub to that. 

4gbs *should *be enough to live without swap, but I'd still make a 4gb swap partition. If I were you, this would be what I'd do:
Shrink G by 4gb 
Make a new, 4gb partition

Go to install, select the Something Else option
Format G as Ext4, give it a mount point of /
Format D as Ext4, give it a mount point of /home
Format the 4gb partition you just made as swap
Install Grub to /dev/sda

You can do all of that from the Ubuntu installer, again, use the something else option.

Hi,

So, I've tried what you've mentioned here, except for GRUB, coz I couldn't find this option anywhere during installation. (Please check attached image)

[IMG]http://i1308.photobucket.com/albums/s606/omer_7/IMG_20130623_194907_zps509ab08a.jpg[/IMG]



And secondly I installed the boot loader information in /dev/sda1/ instead of /dev/sda/ (which when selected would show the complete 500GB hard drive, not the partition)


Now after the installation, this time I got boot menu option (when restarted PC, please see attached image below), but when I would select /dev/sda1/ (for booting windows 7), nothing appears. That means I was unable to log into windows 7 and I could only log into ubuntu. I had to use windows 7 DVD to /fixBoot and /FixMbr. After this, no boot menu is appearing (as before) and my PC again is directly booting into Windows 7 :( :(


[IMG]http://i1308.photobucket.com/albums/s606/omer_7/IMG_20130623_202257_zps6554f1fc.jpg[/IMG]


I think the problem is as mentioned by member in the above post that after installing windows 8 it has written win 8 boot files, and I don't know how to change it to windows 7 boot files.


EDIT: I'm installing Ubuntu 13.04 from a USB (made it bootable by information given on ubuntu website). MY DVD ROM is not working for some reasons :(

---

### Post by oldfred on 2013-06-23
Windows has to have its boot code in a PBR if BIOS/MBR based install. If you installed grub to sda1 you damaged the NTFS PBR or partition boot sector. It keeps a backup which you can restore if you only installed once. Otherwise you have to run Windows repairs.
Grub has to be installed to the MBR of sda as that is how BIOS computers boot.

Fix for most, a few have other issues, better than windows fix in many cases as it also fixes other parameters:
If win7 use small 'system reserved' NTFS partition instead of the partition where windows was installed for win7
This has instructions on using testdisk to repair the install of grub to the boot sector for windows from Ubuntu or Linux LiveCD.
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)
You want to get to this screen:
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery)
OR:
[HowTo] Repair the bootsector of a Windows partition  - YannBuntu
[https://help.ubuntu.com/community/BootSectorFix](https://help.ubuntu.com/community/BootSectorFix)
[http://ubuntuforums.org/showthread.php?t=1926510](http://ubuntuforums.org/showthread.php?t=1926510)

While Vista, applies to all BIOS/MBR Windows systems. But not the new UEFI.
       Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)

---

### Post by omer7 on 2013-06-23
At lastttttt, the issue resolved :D

I'm thankful to @debodas and @oldfred for providing me the assistance. You guys are genius :)


How did the issue resolved:

- Did everything as @debodas said:
- Made a swap partition of about 8GB
- Formatted one drive (I guess G) with Ext4 and used / as mount
- Formatted another drive (I guess D) with EXT4 and used /home as mount
- **And the important step which I didn't do last time, which was causing issue, This time I installed boot loader installation in /dev/sda/, and issue resolved**. Now I can choose whether to log into windows 7 or ubuntu and both are working :D.

Just I would like to ask one last question, whenever I start Ubuntu (after selecting it from boot menu option), there's something like this appears before the ubuntu login screen:

* (some long number is mentioned then) **kvm (disabled by BIOS)** :S ...

What is that?

---

### Post by oldfred on 2013-06-23
The long number may be a UUID for a partition as unique identifier.

KVM probably is this but I have never turned it on or off.
[http://www.linux-kvm.org/page/Main_Page](http://www.linux-kvm.org/page/Main_Page)
*KVM* (for Kernel-based Virtual Machine) is a  full virtualization solution for Linux on x86 hardware containing  virtualization extensions (Intel VT or AMD-V).

---

### Post by omer7 on 2013-06-23
> **oldfred said:**
> The long number may be a UUID for a partition as unique identifier.

KVM probably is this but I have never turned it on or off.
[http://www.linux-kvm.org/page/Main_Page](http://www.linux-kvm.org/page/Main_Page)
*KVM* (for Kernel-based Virtual Machine) is a  full virtualization solution for Linux on x86 hardware containing  virtualization extensions (Intel VT or AMD-V).

Ok. Thank you very much.

I'll check it out in BIOS settings. But even if it is disabled (though I do not know what this option is and/or what it does), Ubuntu is working fine. :)

---

### Post by debodas on 2013-06-23
> **omer7 said:**
> <snip>
- **And the important step which I didn't do last time, which was causing issue, This time I installed boot loader installation in /dev/sda/, and issue resolved**. Now I can choose whether to log into windows 7 or ubuntu and both are working :D.

Grub = the boot loader ;)

---

### Post by omer7 on 2013-06-23
> **debodas said:**
> Grub = the boot loader ;)


Haha... Okay. Thanks bro.

I dint know abt it. I was looking for the word GRUB there :P

---

