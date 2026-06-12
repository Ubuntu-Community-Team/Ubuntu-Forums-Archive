---
title: "Installed Wubi to have Ubuntu Alongside Windows, now what"
date: 2012-07-19
forum: Installation &amp; Upgrades
---

### Post by moogs37 on 2012-07-19
Like the title states, I have installed Ubuntu using Wubi to run alongside my Windows 7 OS on my HP Pavillion g7.
 
I am curious as to how this exactly works?  Where is the information stored?  I do not see any storage usage/partition on my harddrive.
 
I was wanting to actually "see" what goes where.
 
I was thinking of perhaps reinstalling?  Any suggestions?

---

### Post by darkod on 2012-07-19
I don't use wubi, but something is confusing me. It's either wubi inside windows or ubuntu on its own partition along side windows. Not both.

In any case, windows can't open linux partitions, not by default. So people usually make common ntfs partition for data that needs to be accessed from both OSs. Again, I have no idea how that would work from wubi because it's like a virtual system inside windows.

I only use separate ubuntu on its own partition and highly recommend that. Wubi is only for short tests anyway, not for long term usage.

If you do have the ubuntu iso burnt on a cd, boot with that cd in live mode (Try Ubuntu), open terminal and try listing the disks partitions with:
```
sudo fdisk -l
sudo parted -l
```

That will show whether the disk has only ntfs partitions, or linux partitions too.

---

### Post by mastablasta on 2012-07-19
wubi installs into a large virtual file inside widnows. so in windows you will only see that one large file i believe. while if you boot to your installed linux you will see various directories.
 
note in linux everything is in directory. even media is in directory.
 
also what exactly do you want to do?

---

### Post by moogs37 on 2012-07-19
> **mastablasta said:**
> wubi installs into a large virtual file inside widnows. so in windows you will only see that one large file i believe. while if you boot to your installed linux you will see various directories.
 
note in linux everything is in directory. even media is in directory.
 
also what exactly do you want to do?
 
I was wanting to have Windows 7, Ubuntu, and Fedora on my computer on different partitions so they can use each partition to their own needs accordingly.  Is this possible?

---

### Post by moogs37 on 2012-07-19
> **darkod said:**
> I don't use wubi, but something is confusing me. It's either wubi inside windows or ubuntu on its own partition along side windows. Not both.
 
In any case, windows can't open linux partitions, not by default. So people usually make common ntfs partition for data that needs to be accessed from both OSs. Again, I have no idea how that would work from wubi because it's like a virtual system inside windows.
 
I only use separate ubuntu on its own partition and highly recommend that. Wubi is only for short tests anyway, not for long term usage.
 
If you do have the ubuntu iso burnt on a cd, boot with that cd in live mode (Try Ubuntu), open terminal and try listing the disks partitions with:
```
sudo fdisk -l
sudo parted -l
```
 
That will show whether the disk has only ntfs partitions, or linux partitions too.
 
 
Thanks for this.  I will look into it when I get home and open up my computer.  I will definitely have to uninstall Wubi, and create and install a partition just for itself.

---

### Post by darkod on 2012-07-19
> **moogs37 said:**
> I was wanting to have Windows 7, Ubuntu, and Fedora on my computer on different partitions so they can use each partition to their own needs accordingly.  Is this possible?

Yes, it is. But not with wubi.
Burn a cd with the ubuntu image and with the fedora image, and install on its own partitions. Forget the wubi.exe completely.

---

### Post by moogs37 on 2012-07-19
> **darkod said:**
> Yes, it is. But not with wubi.
Burn a cd with the ubuntu image and with the fedora image, and install on its own partitions. Forget the wubi.exe completely.
 
I will definitely get rid of the wubi.exe.  
 
I think the main problem I am having is the partitions.   I have searched before but have found no exact manual on how to create a partition for a linux OS.  Do you know where I can find one?  Or can you tell me how to do it?

---

### Post by Frogs Hair on 2012-07-19
The link may be helpful. Like the tutorial I created the space used for Ubuntu from Windows disk management. There is no longer an install alongside option in 12.04 . [http://www.liberiangeek.net/2012/04/dual-boot-windows-7-and-ubuntu-12-04-precise-pangolin/](http://www.liberiangeek.net/2012/04/dual-boot-windows-7-and-ubuntu-12-04-precise-pangolin/)

---

### Post by darkod on 2012-07-19
> **moogs37 said:**
> I will definitely get rid of the wubi.exe.  
 
I think the main problem I am having is the partitions.   I have searched before but have found no exact manual on how to create a partition for a linux OS.  Do you know where I can find one?  Or can you tell me how to do it?

You can create partitions during the install using the manual partitioning option. But you need to have unallocated space for that. If windows is taking the whole disk right now, shrink it with windows Disk Management first and reboot few times. Only then continue with linux installs.

In general, two partitions are enough:
The main system partition, root, which has mount point /
The swap partition, either 2GB or 1.5 x RAM size if you plan to hibernate.

The swap can be shared between more linux systems, ubuntu and fedora can share it so you need to created only one. During the second install just tell it to use the existing swap partition as swap.

I would install first fedora and then ubuntu so that the ubuntu bootloader grub2 can be the last one installed on the MBR (/dev/sda).

EDIT PS: The tutorial posted above should work out for you. Just make sure to plan whether the partitions for linux will be primary or logical. Since you plan to install fedora too, don't forget the limitation that you can have only 4 primary partitions. So it's best to create the linux partitions as logicals.

---

### Post by moogs37 on 2012-07-19
> **darkod said:**
> You can create partitions during the install using the manual partitioning option. But you need to have unallocated space for that. If windows is taking the whole disk right now, shrink it with windows Disk Management first and reboot few times. Only then continue with linux installs.
 
In general, two partitions are enough:
The main system partition, root, which has mount point /
The swap partition, either 2GB or 1.5 x RAM size if you plan to hibernate.
 
The swap can be shared between more linux systems, ubuntu and fedora can share it so you need to created only one. During the second install just tell it to use the existing swap partition as swap.
 
I would install first fedora and then ubuntu so that the ubuntu bootloader grub2 can be the last one installed on the MBR (/dev/sda).
 
EDIT PS: The tutorial posted above should work out for you. Just make sure to plan whether the partitions for linux will be primary or logical. Since you plan to install fedora too, don't forget the limitation that you can have only 4 primary partitions. So it's best to create the linux partitions as logicals.
 
How much space should I have for Fedora and Ubuntu, each?  I have a 500 gb hd.

---

### Post by moogs37 on 2012-07-19
> **Frogs Hair said:**
> The link may be helpful. Like the tutorial I created the space used for Ubuntu from Windows disk management. There is no longer an install alongside option in 12.04 . [http://www.liberiangeek.net/2012/04/dual-boot-windows-7-and-ubuntu-12-04-precise-pangolin/](http://www.liberiangeek.net/2012/04/dual-boot-windows-7-and-ubuntu-12-04-precise-pangolin/)
 
As I can see from the link you gave me, I am to create a parition by running disk management and just making "free space"?  I always thought I had to choose the make another drive option so I was trying to install it on D:/.

---

### Post by darkod on 2012-07-19
> **moogs37 said:**
> How much space should I have for Fedora and Ubuntu, each?  I have a 500 gb hd.

That's up to you. The root partition is usually OK with 15-20GB. If you have the Home folders inside it, the more large data you store there, the more space you need.

You could also have one big ntfs partition and store all large data that needs to be shared in there. That way all three OSs can access it. And in that case the root partitions can be small.

This planning depends on you.

---

### Post by moogs37 on 2012-07-19
> **darkod said:**
> You can create partitions during the install using the manual partitioning option. But you need to have unallocated space for that. If windows is taking the whole disk right now, shrink it with windows Disk Management first and reboot few times. Only then continue with linux installs.
 
In general, two partitions are enough:
The main system partition, root, which has mount point /
The swap partition, either 2GB or 1.5 x RAM size if you plan to hibernate.
 
The swap can be shared between more linux systems, ubuntu and fedora can share it so you need to created only one. During the second install just tell it to use the existing swap partition as swap.
 
I would install first fedora and then ubuntu so that the ubuntu bootloader grub2 can be the last one installed on the MBR (/dev/sda).
 
EDIT PS: The tutorial posted above should work out for you. Just make sure to plan whether the partitions for linux will be primary or logical. Since you plan to install fedora too, don't forget the limitation that you can have only 4 primary partitions. So it's best to create the linux partitions as logicals.
 
 
Question, for the swap partition you said either 2GB or 1.5 X RAM size.  If I have 4 GB ram, would this make the swap partition to 8 GB or 6 GB?

---

### Post by moogs37 on 2012-07-19
> **darkod said:**
> That's up to you. The root partition is usually OK with 15-20GB. If you have the Home folders inside it, the more large data you store there, the more space you need.
 
You could also have one big ntfs partition and store all large data that needs to be shared in there. That way all three OSs can access it. And in that case the root partitions can be small.
 
This planning depends on you.
 
I was thinking 50-100 gb for each linux distro.  Is this too much?

---

### Post by darkod on 2012-07-19
> **moogs37 said:**
> As I can see from the link you gave me, I am to create a parition by running disk management and just making "free space"?  I always thought I had to choose the make another drive option so I was trying to install it on D:/.

Not exactly. Shrinking the windows partition creates unallocated, unpartitioned space on the disk. It does not create any partitions, and it shouldn't. Windows can't create linux partitions so don't even try to create partitions in Disk Management. Just use it to shrink C: to the size you want, and leave the rest as unallocated.

As the tutorial shows later, you will create the linux partitions manually during the linux installations.

---

### Post by darkod on 2012-07-19
6GB should be OK for swap.
50-100GB for linxu root is more than plenty, it depends on the data you plan to keep there and how you want to organize all of it. As I mentioned, you can have a root of 20GB and the data on common partition.

---

### Post by moogs37 on 2012-07-19
> **darkod said:**
> 6GB should be OK for swap.
50-100GB for linxu root is more than plenty, it depends on the data you plan to keep there and how you want to organize all of it. As I mentioned, you can have a root of 20GB and the data on common partition.
 
Okay, so I am going to unallocate the partition which I created last night.  I figured it would be something like this that is causing me problems.
 
When I run Fedora and click install, which partition option should I choose?  
 
My options are:
1) use all space (cannot use this option because of my requirements);
2) replace existing linux systems (cannot choose this because I will not have an existing linux system);
3) shrink current system (unsure if I want to do this as I heard it could make the harddrive not be able to load up the OS);
4) use free space (possibility); or
5) create custom layout (the other possibility).
 
I am guessing I should either choose option 4 or 5.  Darko, what is your suggestion when I encounter this screen?

---

### Post by darkod on 2012-07-19
Custom.

If you tell it to use free space it will use all of it, and you need some for ubuntu too.

Use Custom so that you can control the partition sizes yourself, not the automatic methods.

---

### Post by moogs37 on 2012-07-19
> **darkod said:**
> Custom.
 
If you tell it to use free space it will use all of it, and you need some for ubuntu too.
 
Use Custom so that you can control the partition sizes yourself, not the automatic methods.
 
Could I choose the use free space and then allocate more space for Ubuntu later in Window's Disk Management?

---

### Post by tmaranets on 2012-07-19
If there is nothing wrong, then don't install again. You should keep Wubi just in case anything wrong happens in Ubuntu

---

### Post by darkod on 2012-07-19
> **moogs37 said:**
> Could I choose the use free space and then allocate more space for Ubuntu later in Window's Disk Management?

You could, but I don't see the point. Are you afraid to partition manually? As I said, it gives you best control on partition sizes.

Like this, fedora will take all the unallocated space, which is probably too much for fedora, and then you have to shrink win7 again to make unallocated space for ubuntu. By shrinking win7 you can leave it with not enough space to work properly, you need to keep an eye on that too. You know how hungry for space win7 is.

---

### Post by moogs37 on 2012-07-19
> **darkod said:**
> You could, but I don't see the point. Are you afraid to partition manually? As I said, it gives you best control on partition sizes.
 
Like this, fedora will take all the unallocated space, which is probably too much for fedora, and then you have to shrink win7 again to make unallocated space for ubuntu. By shrinking win7 you can leave it with not enough space to work properly, you need to keep an eye on that too. You know how hungry for space win7 is.
 
Makes sense.  Thanks for your advice.  I am a little apprehensive, not sure exactly what variables I should put in the custom screen.  Do you have any advice on what to create and where?

---

### Post by darkod on 2012-07-19
> **moogs37 said:**
> Makes sense.  Thanks for your advice.  I am a little apprehensive, not sure exactly what variables I should put in the custom screen.  Do you have any advice on what to create and where?

That tutorial with screenshots covers that too. And we discussed it. Two partitions, root and swap.
Swap of 6GB.
Root of 20GB, or 50GB, up to you.

Then when installing ubuntu, it can use the same swap, just create different 20GB root partition.

The rest of the unallocated space you can make common ntfs partition that all OSs can read. But you do that after all installations are done, not during the linux installations.

---

### Post by moogs37 on 2012-07-19
> **darkod said:**
> That tutorial with screenshots covers that too. And we discussed it. Two partitions, root and swap.
Swap of 6GB.
Root of 20GB, or 50GB, up to you.

Then when installing ubuntu, it can use the same swap, just create different 20GB root partition.

The rest of the unallocated space you can make common ntfs partition that all OSs can read. But you do that after all installations are done, not during the linux installations.


Going to install it now.  Will let you know how it goes.

---

### Post by moogs37 on 2012-07-19
Tried to install and it still says that I don't have enough space.  

Per disk management in Windows, I have the following:
1) system - 199 mb ntfs healthy (system)
2) c:/ - 350 gb ntfs healthy (boot, page file, crash dump)
3) unallocated - 115.57 gb

In the config setup it showed the following information when I was trying to select partitions-
1) sda1 - 0
2) sda2 - 199 mb
3) sda3 - 350 gb
4) sda4 - 115.57 gba
5) a couple mb free space

Any suggestions?

---

### Post by oldfred on 2012-07-19
You say the 115.57 is unallocated and then say it is sda4. It cannot be both. Unallocated has no partition.

With MBR partitions you can only have 4 primary partitions, but one primary can be converted to an extended which can hold many logical partitions.
Basics of partitions:
[http://en.wikipedia.org/wiki/Disk_partitioning](http://en.wikipedia.org/wiki/Disk_partitioning)
[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

Fedora defaults to using LVM which is a logical partitioning scheme. Its advantage is you you span multiple partitions or even drives and easily repartition on the fly. But it adds another level of complexity  and cannot use standard partitioning tools but LVM tools. It then also creates a separate /boot outside the LVM.
Many just trying Fedora just install to a partition not using LVM.

Some also create shared partitions for data, so all data can be shared across all systems. If using Windows you may want a NTFS shared partition. If just linux you can use ext4.

If you use the LVM partitioning in Fedora, you have to install the lvm2 package in Ubuntu to see it.

Is able to search LVM partitions if the LVM2 package is install, Fedora needs to be mounted to see it with os-prober
# ("apt-get install lvm2" in debian based distros)

---

### Post by moogs37 on 2012-07-19
I installed Fedora but... I just got an error during the installation of the bootloader:

There was an error installing the bootloader.  The system may not be bootable??  Now when I start up the computer, it goes to the Windows screen, then shuts off!

What now?
[COLOR=Silver][/COLOR]

---

### Post by oldfred on 2012-07-19
Post boot info script or BootInfo from this:

Boot Repair -Also handles LVM, GPT and separate /boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration.

---

### Post by moogs37 on 2012-07-19
[http://pastebin.com/wKkZpPS8](http://pastebin.com/wKkZpPS8)

---

### Post by moogs37 on 2012-07-19
Irc channel told me to do reinstall with DVD. Doing that now.

---

### Post by oldfred on 2012-07-20
Your boot script shows a Windows issue. Your partitions are shown as SFS which is in Windows dynamic partitions. You must have tried to create partitions in Windows. When you get to more than the MBR(msdos) limit of 4 primary partitions Windows does not use the standard extended partition but converts to dynamic. Dynamic partition will not work with Linux.

Dynamic volume is a Microsoft proprietary format developed together with Veritas (now acquired by Symantec) for logical volumes.
You may be use a third-party tool, such as Partition Wizard MiniTool or EASEUS to convert a convert a dynamic disk to a basic disk without having to delete or format them.
I've never used any of these and so I can't be sure they will work.Be sure to have good backups as any major partition change has risks.

Used EASEUS Partition Master -  free version includes conversion
[http://ubuntuforums.org/showthread.php?t=1692248](http://ubuntuforums.org/showthread.php?t=1692248)
EASEUS Partition Master - The free home edition converted both dynamic partitions into basic partitions in less than 5 minutes!!
[http://www.partition-tool.com/personal.htm](http://www.partition-tool.com/personal.htm)

Several users have used this, it has a liveCD download to use but you have to use the non-free version:
MiniTool Partition Wizard Professional Edition 5.2 to convert without loss of data the disk from dynamic disk to a basic disk.
also used Partition Wizard to set an existing partition logical instead of primary
Converted from dynamic with MiniTool, & repaired windows
[http://ubuntuforums.org/showthread.php?t=1779529](http://ubuntuforums.org/showthread.php?t=1779529)
[http://www.partitionwizard.com/convertpartition/convert-to-basic-disk.html](http://www.partitionwizard.com/convertpartition/convert-to-basic-disk.html)

---

### Post by darkod on 2012-07-20
Man, you really made a mess. :)

First of all, we said hundred times to only shrink windows and leave the space as unallocated, not to create any partition from windows. But it seems you did create a partition in the 115GB space.

Then, I guess you tried to create more than 4 partitions in windows, in which case it converts the disk in Dynamic without warning you. You see in the results, sda2 and sda3 are SFS type, not NTFS.

SFS is Microsoft format for dynamic disks, and usually linux doesn't work good with it. I don't know about fedora, but ubuntu can't handle dynamic disks.

I don't know how fedora ended up taking sda1. That's why I said the manual method, so you can control where you make the partitions, and I assumed you will make them after the windows partitions, not in front of them. This could be the reason why windows shuts off, it seems moved around.

PS. I see oldfred posted a similar post, it has instructions how to convert the disk back to basic, as it should be. Lets see if that helps.

---

### Post by moogs37 on 2012-07-20
How do I do this if I cannot load up windows?

---

