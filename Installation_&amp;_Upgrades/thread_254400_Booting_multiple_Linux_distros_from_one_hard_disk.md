---
title: "Booting multiple Linux distros from one hard disk"
date: 2006-09-09
forum: Installation &amp; Upgrades
---

### Post by svetlo56 on 2006-09-09
I would like to put several Linux distros on one hard disk, with or without M$. I do know that there's a Grub (or lilo) boot loader but do not know how to set it up. I did go to Grub web site but since I do not have much experience with compiling, I would like to ask the community if there's a simple guide on this topic. Needless to say I did plenty of Googling and Asking but could not get a simple answer. Thanks

---

### Post by mssever on 2006-09-10
The way Ubuntu works--and probably most other distros--the installer auto-detects the OSes on your machine and configures/installs Grub appropriately. It should be fairly painless. Of course, make sure that you nstall at least one Linux after Windows, because Win doesn't play nice with Grub.

---

### Post by confused57 on 2006-09-10
> **svetlo56 said:**
> I would like to put several Linux distros on one hard disk, with or without M$. I do know that there's a Grub (or lilo) boot loader but do not know how to set it up. I did go to Grub web site but since I do not have much experience with compiling, I would like to ask the community if there's a simple guide on this topic. Needless to say I did plenty of Googling and Asking but could not get a simple answer. Thanks
There's probably several ways you could set up multi-booting several Linus distros.  A few basics you need to be aware of is that Windows has to be on a primary partition and you're only allowed 4 primary partitions on a hard drive...so you'll need to plan beforehand how you want to set your system up, partition sizes, etc.  Linux can be installed on a logical partition...you can have many logical partitions within one extended primary partition, it's confusing at first, I know.
   What you'd probably want to do is install Windows on the first primary partition, then Ubuntu on the 2nd primary partition and select swap as a logical partition, the installer will automatically create an extended partition(usually hda2) and swap will be a logical partition within the extended partition.  The default install of Ubuntu is to set swap up as a logical partition.  Ubuntu will install grub to the Windows mbr, which will allow you to boot either OS.
   To install other Linux OS, you'd need to free up unallocated space either with the distro installer or probably better with the gparted live cd:
[http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828)
The gparted live cd will give you a graphical display of your partition tables and you can resize, create, delete, move,etc partitions.
  Any additional Linux distros can be installed on a logical partition(you can use the one swap partition for all your distros), just set the mountpoint as root(/) for the OS.  I prefer to install grub to the root partition of the distro I'm installing, then add an entry in Dapper's /boot/grub/menu.lst to boot the OS.  For example, I installed Edgy to hda6 and added the following entry to grub:
title          Edgy
rootnoverify  (hd0,5)
chainloader +1

  You can also choose to install grub to the mbr of any distros that you install, but you'll need to know how to add entries to your menu.lst in case all the OS are not detected by the OS.
You can always reinstall Dapper grub with the live cd:
[http://www.ubuntuforums.org/showthread.php?t=224351](http://www.ubuntuforums.org/showthread.php?t=224351)

  It's pretty easy once you get the hang of it, I've had my share of trial and error failed attempts...but hope I've given you some idea of what to expect & to research.

  Here's a guide for planning partitions:
[http://psychocats.net/ubuntu/partitioning.html](http://psychocats.net/ubuntu/partitioning.html)

  Hope this explains a little, I sort of threw it together...the forum is up & down so much, I'm afraid that by clicking preview I'd lose my connection and everything I'd typed...therefore I've gotten to where I just click submit & edit later when the forum is up.

---

### Post by svetlo56 on 2006-09-22
I installed M$ XP and then Ubuntu, and it was good. Then I tried another distro (PCLinuxOS, Freespire and SUSE). Each time the second distro happily installed it's GRUB or Lilo into the mbr and conveniently ignored the first distro. I tried to install the second distro on one of partitions, but the second distro changed the partitions by itself without asking any question and sometimes just went and overwrote the first distro. So I couldn't get two distros and M$ to cooperate and it was no good. 

Now I am stuck. One if solutions proposed was to install **each distro's mbr on individual partitions** and then edit the GRUB appropriateyl. But I do not see any options to do so when installing a distro. Help!!!

---

### Post by confused57 on 2006-09-22
> **svetlo56 said:**
> I installed M$ XP and then Ubuntu, and it was good. Then I tried another distro (PCLinuxOS, Freespire and SUSE). Each time the second distro happily installed it's GRUB or Lilo into the mbr and conveniently ignored the first distro. I tried to install the second distro on one of partitions, but the second distro changed the partitions by itself without asking any question and sometimes just went and overwrote the first distro. So I couldn't get two distros and M$ to cooperate and it was no good. 

Now I am stuck. One if solutions proposed was to install **each distro's mbr on individual partitions** and then edit the GRUB appropriateyl. But I do not see any options to do so when installing a distro. Help!!!

What you could do is write down the exact grub entry to boot the Linux OS that you installed(also, note the entry to boot Windows, just in case).  Then you can restore the Dapper grub using the live cd:
[http://www.ubuntuforums.org/showthread.php?t=224351](http://www.ubuntuforums.org/showthread.php?t=224351)

Then add the entries to your /boot/grub/menu.lst in Dapper(if it wasn't added automatically by the live cd):
```
cd /boot/grub
sudo cp menu.lst menu.lst_backup
gksudo gedit menu.lst
```

This will open your grub menu.lst & you can add the entry to boot the new Linux OS.

---

### Post by Herman on 2006-09-22
Yes, I agree, and also, here are a few examples of different kinds of operating system entries for your menu.lst file for multiple boot ing Linux,

Operating System Entries for Multiple Booting More Linux Systems............................[GO]("http://users.bigpond.net.au/hermanzone/p15.htm#Operating_System_Entries_for_Multiple_Booting_More_Linux_Systems")

Regards, Herman :D

---

### Post by Herman on 2006-09-22
>  Now I am stuck. One if solutions proposed was to install **each distro's mbr on individual partitions** and then edit the GRUB appropriateyl. But I do not see any options to do so when installing a distro. Help!!!To use the chainloader command, in some distros, you may be offered the choice of having the bootloader's IPL code written to the first sector of the partition or to MBR. Having it written to the first sector of the partition means you can chainload it with a third party boot manager, or with Grub from another partition. (Ubuntu in your case).
The best way is to do it after the install even if you installed Grub to MBR during installation is to open a grub shell and do it the same way as [installing Grub to MBR]("http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD"), but replace '(hd0)' with (hd0,y), (Where: 'y' is the grub number for the operating system's partition.
You might also do it the quick way with the command 'sudo grub-install hdx', where 'x' is the letter of the partition you want grub installed to. [ install Grub's IPL to the first sector]("http://users.bigpond.net.au/hermanzone/p6.htm#Can_a_bootloaders_IPL_be_installed_in_a_partition")

The easiest way is to ignore all the problems along the way with getting other distros to recognize and add each other to various menus, and where they want to install Grub's IPL to, and just install Ubuntu last. Ubuntu will probably recognize them all and add them all automatically for you. (Because Ubuntu is the best) :D
I forget if just re-installing Grub in Ubuntu or using some grub command to re-write your menu.lst will automatically add all the other distros, but I don't think so.  

The second easiest way is to use the the 'configfile' command, (the third style of multiple boot menu entry in the link I already gave).  That's a really good command for multi booting. That way you don't need to install the bootloader's IPL anywhere. It saves a little work. You will need to modify the path and name of the configfile for many of the other distros. They do not all have a configfile in /boot/grub, named menu.lst. For example, some distor might have just a /GRUB directory (in capital letters), with a file in it named /GRUB/grub.conf or something else like that. 
So you will need to be prepared to find out and alter the exact details following the config command to suit whatever distro you are booting. It's not too hard. :D

Regards, Herman :D

---

### Post by svetlo56 on 2006-09-23
The problem is that I do not see an option to force any of the distros to install on a particular partition. If I had that option, then I would go and edit the original GRUB installed by the first distro. And the answer to the question about any distro installing it's GRUB into the mbr of ITS partition would solve the problem. 

So the question boils down to how to persuade a distro not to mess with anything else but the partition it was told to install itself, and install its GRUB to this particular partition and LEAVE THE OTHER PARTITIONS ALONE!!!!

So the question is HOW TO FORCE A DISTRO TO INSTALL ITS GRUB TO ONE PARTITION AND DON'T MESS WITH ANYTHING ELSE.

Or maybe I am getting everything wrong....I am trying my best to make things simple....

---

### Post by Herman on 2006-09-23
> The problem is that I do not see an option to force any of the distros to install on a particular partition. If I had that option, then I would go and edit the original GRUB installed by the first distro. And the answer to the question about any distro installing it's GRUB into the mbr of ITS partition would solve the problem. 
So the question boils down to how to persuade a distro not to mess with anything else but the partition it was told to install itself, and install its GRUB to this particular partition and LEAVE THE OTHER PARTITIONS ALONE!!!!
So the question is HOW TO FORCE A DISTRO TO INSTALL ITS GRUB TO ONE PARTITION AND DON'T MESS WITH ANYTHING ELSE.
Or maybe I am getting everything wrong....I am trying my best to make things simple.... It IS simple- just don't worry about it. :D 
LET each distro install it's bootloader's IPL to MBR. Your MBR will never wear out! Who cares! :D

There is only one MBR for each hard disk, the MBR is in the first sector of the first track.  The MBR is not part of any operating system's partition. The entire first track (63 sectors) are not included in any operating system's partition. 
The first partition does not begin until after that. Just do 'sudo fdisk -lu', and you will be able to see that.  
Each partition has it's own boot sector.  Each partition's boot sector can have an IPL for a bootloader installed to it. 

I would just install all my distros that I want and I would not worry about where they install their bootloader's IPL code. Then I would just install a bootloader to MBR that I finally want to keep (grub from my main Ubuntu install probably), last and edit the menu.lst of that one with 'configfile' commands for the other OSes. I would install Lilo or Grub to the boot sectors of the partitions too in case I ever want to chainload them someday for some reason. :D

I don't know why you are worried about it at all, the MBR is just another sector of your hard disk that can be written to and then written over as many times as you like just like any other sector on your hard disk. It's made of the same material. Your hard disk will probably have a bearing failure long before the MBR or any other sector will wear out from writting to it too much. Just have fun and don't worry about it. Go ahead and install all the OSes you want. Shake off the shackles of commercial software and all it's associated propaganda and lies! Be free! Learn things. Enjoy your freedom!  :D

Regards, Herman

---

### Post by Herman on 2006-09-23
How to back up and restore your MBR..............................................................................[GO]("http://users.bigpond.net.au/hermanzone/p15.htm#How_to_back_up_and_restore_your_MBR")
MBR backup and restore.............................................................................................[GO ]("http://users.bigpond.net.au/hermanzone/p13.htm#mbr_dd")
     
Here are a couple of links about how to back up and restore your MBR if you would be interested in doing that. I only recommend backing up the bootloader's IPL code area of the MBR though, (first 446 bytes) _not_ the partition table.
The reason for that is, you will be partitioning your disk and writting changes to the partition table and creating new filesystems to match the new partition table. You would not then want to restore the old partition table because that would not fit your new filesystems.
As long as you only back up the first 446 bytes and not the entire 512 bytes you'll be fine. :D
That would be another way around your problem, if you find that an interesting thing to try. Really, it doesn't make any difference how you do it, but at least now you know another way. :D

Regards, Herman :D

---

