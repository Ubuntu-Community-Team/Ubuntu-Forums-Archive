---
title: "Explanation For Failed Grub Installation"
date: 2012-12-03
forum: Installation &amp; Upgrades
---

### Post by Brando569 on 2012-12-03
I am an experienced Linux user (I have been running Arch Linux for over 2 years, I started out on Ubuntu 5.04 many years ago :) ) and last night I attempted to install Kubuntu 12.10 on my girlfriend's HP Pavilion G7 and everything went smoothly until the very end of the installation where it installs Grub. The installer failed due to grub and I tried to run **sudo grub-install /dev/sda** manually and it said that /boot/grub wasn't accessible during boot, so instead of installing it to the MBR I attempted to install it to the partition (sda4) but got the same error. I was going to create a separate boot partition but was already at the maximum of 4 primary partitions since the HP Tools (factory image, diagnostics and all that good stuff)occupied the first partition, Windows 7 boot files occupied the second partition, Windows 7 itself occupied the third partition and Kubuntu occupied the 4th partition.

After looking up a few solutions, none applied to her and were all about (fake/software) RAID. So giving up for the moment, I rebooted only to find that Windows 7 would get to the "loading" screen for about a minute or two then BSOD and reboot. I tried to run start up repair but W7 couldn't detect the installation, so I tried the Windows installation disk and it wouldn't even detect the stupid HDD!

I booted up the Kubuntu live dvd once again and made sure that the HDD hadn't spontaneously died or got corrupted, everything was there. I went into the partition editor and noticed that the EXT4 partition that Kubuntu was installed on said that it had a corrupted Superblock. On a whim (since it was getting really late and I had to go to sleep)I deleted the EXT4 partiton and rebooted. To my surprise Windows booted like it did before I even attempted any of this.

In my years of using Linux I've have never seen something like this happen before. Does anyone know what would cause Windows 7 to BSOD and have the Installer not detect the HDD? Also how can I get Grub to install properly since she is allowing me to do it again and I want to get everything right this time so that I will give a good impression of the stability of Linux?

---

### Post by darkod on 2012-12-03
Does the laptop use Intel SRT? That is sort of combination of hdd + ssd as fast cache disk. They are sort of joined together, and partitioning it will not produce the same results as a single disk.

Another possibility is that the kubuntu partition was created with some error. Partitioning tools usually display blank disk (without any partitions) if there is error in the partition table. Deleting that partition made the error go away, so everything worked again.

And if you create the linux partition as logical, not primary, you can have more than 4. The logical partitions on the disk must be next to each other, and in that case one extended partition is created that holds them like a container. The disk can have 3 primary + 1 extended partitions. But having separate /boot is not needed, especially if that /boot is not close to the start of the disk. It is useful only in special cases and most often when close to the start. In 99% of cases you don't need it as separate partition.

The weird partitioning result and the grub failure could point to Intel SRT since in that case the hdd+ssd are in a sort of fakeraid.

---

### Post by oldfred on 2012-12-03
+1 on Darko's comments.

We also are seeing more & more UEFI systems.

Best to see exactly where you are at.

       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[http://sourceforge.net/p/boot-repair/home/Home/](http://sourceforge.net/p/boot-repair/home/Home/)
[https://help.ubuntu.com/community/UbuntuSecureRemix](https://help.ubuntu.com/community/UbuntuSecureRemix)

---

### Post by Brando569 on 2012-12-03
It's not an Intel SRT drive and neither is it a UEFI system (unless its unlisted).

Here's the product page: [http://h10025.www1.hp.com/ewfrf/wc/document?docname=c02789982&tmp_task=prodinfoCategory&cc=us&dlc=en&lang=en&lc=en&product=5078509](http://h10025.www1.hp.com/ewfrf/wc/document?docname=c02789982&tmp_task=prodinfoCategory&cc=us&dlc=en&lang=en&lc=en&product=5078509)

Any other ideas? Its possible that the partition was erroneously created.

---

### Post by darkod on 2012-12-03
In that case you can try creating the partition again and give it another shot.

If you tried to shrink the win7 partition using the installer, that might have created wrongly the kubuntu partition somehow. In order not to break win7, you should shrink its partition with windows Disk Management.

If right now you have the unallocated space created by deleting sda4, just go ahead.
If win7 is taking the whole disk, shrink it with Disk Management, not the kubuntu installer.

---

### Post by Brando569 on 2012-12-03
I had the thought to allocate 50 GB for Kubtuntu when I had reinstalled Windows 7 a week or two ago, so the error wasn't caused by shrinking the partition. Maybe Partition Editor screwed up, I'll used parted or fdisk next time.

I'm not going to have access to the laptop for another two weeks so I can't really test anything on it :-\

---

### Post by darkod on 2012-12-03
I prefer parted, even though it's command line, or Gparted.

I have seen it mentioned that fdisk can mess up partition creation (maybe that was only for older versions).

But since you were wise to leave unallocated space, creating the partition during the install should have worked out just fine. I use manual partitioning and create partitions during the install, not in advance.
Of course, if I am reusing existing partitions then they already exist.

---

### Post by oldfred on 2012-12-03
May be best to post this. If gpt partitioned and first partition is efi then it is UEFI.

If MBR(msdos) then you may have the 4 primary partition issue.

---

### Post by darkod on 2012-12-03
Also, another thing that can mess it up for you and needs attention, open Disk Management and make sure the disk is Basic, not Dynamic. Just in case...

Dynamic disks are MS format and linux won't play nice with them.

---

### Post by oldfred on 2012-12-03
I forgot the command in the previous post, this will give us some clues.

       sudo parted /dev/sda unit s print

---

### Post by Brando569 on 2012-12-04
> **oldfred said:**
> May be best to post this. If gpt partitioned and first partition is efi then it is UEFI.

If MBR(msdos) then you may have the 4 primary partition issue.

It's definitely MBR, I know that for a fact. 

> **darkod said:**
> Also, another thing that can mess it up for you and needs attention, open Disk Management and make sure the disk is Basic, not Dynamic. Just in case...

Dynamic disks are MS format and linux won't play nice with them.

I'll have her check it out later on today to see what they're set as. 

I have an idea that it may be something with the HP Tools partition that is causing errors. I know these OEM diagnostic/tools partitions are always first and they're usually not a FAT(16/32) or NTFS partition, half the time they're marked as hidden and don't show up at all except for a small MB or 2 partition.

---

### Post by Brando569 on 2012-12-05
I asked her last night and the first three partitions (HP Tools, Windows Boot and Windows System) are all set as dynamic.

---

### Post by oldfred on 2012-12-05
Dynamic complicated things. Windows creates dynamic partitions whenever you try to create more than the 4 primary partitions allowed in MBR. But per Microsoft it is a one way conversion. Microsofts suggestion is back up everything (which you should anyway) and erase drive, repartition and restore data.

Some third party tools offer conversion. They used to offer it in the free versions, but it looks like they all have converted to only the paid version now has dynamic partition conversion. You may find the older versions offered on some of the software download sites.
       Dynamic volume is a Microsoft proprietary format developed together with Veritas (now acquired by Symantec) for logical volumes.
You may be use a third-party tool, such as Partition Wizard MiniTool or EASEUS to convert a convert a dynamic disk to a basic disk without having to delete or format them.
I've never used any of these and so I can't be sure they will work.Be sure to have good backups as any major partition change has risks.

   Used EASEUS Partition Master -  free version used to  include conversion
[http://ubuntuforums.org/showthread.php?t=1692248](http://ubuntuforums.org/showthread.php?t=1692248)
EASEUS Partition Master - The free home edition converted both dynamic partitions into basic partitions in less than 5 minutes!!
[http://www.partition-tool.com/personal.htm](http://www.partition-tool.com/personal.htm)

   Several users have used this, it has a liveCD download to use but you have to use the non-free version:
MiniTool Partition Wizard Professional Edition 5.2 to convert without loss of data the disk from dynamic disk to a basic disk.
also used Partition Wizard to set an existing partition logical instead of primary
Converted from dynamic with MiniTool, & repaired windows
[http://ubuntuforums.org/showthread.php?t=1779529](http://ubuntuforums.org/showthread.php?t=1779529)
[http://www.partitionwizard.com/convertpartition/convert-to-basic-disk.html](http://www.partitionwizard.com/convertpartition/convert-to-basic-disk.html)

   Posts by oldfred & srs5694
[http://ubuntuforums.org/showthread.php?t=1705481](http://ubuntuforums.org/showthread.php?t=1705481)
SFS converting:
[http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk.html](http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk.html)
Post 96 using sfdisk - must have only 4 partitions
[http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk-10.html](http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk-10.html)
[http://support.microsoft.com/kb/309044](http://support.microsoft.com/kb/309044)
Also used testdisk
[http://ubuntuforums.org/showthread.php?t=1675420](http://ubuntuforums.org/showthread.php?t=1675420)
Used testdisk but see caveats in Post#7:
[http://ubuntuforums.org/showthread.php?t=1669418](http://ubuntuforums.org/showthread.php?t=1669418)

   EASEUS Partition Master 
[http://www.partition-tool.com/personal.htm](http://www.partition-tool.com/personal.htm)
Partition Wizard
[http://www.partitionwizard.com/free-partition-manager.html](http://www.partitionwizard.com/free-partition-manager.html)

---

### Post by Brando569 on 2012-12-05
Thanks for the info. I'd rather not have to install Windows again considering that I just did it about two weeks ago :-/ if it comes down to it I'll use that Live CD that you mentioned.

The thing I still don't understand is what Dynamic NTFS partitions should affect an EXT4 partition when they're all primary, not extended, partitions. What really threw me through a loop was that Grub wouldn't install anywhere, even to an EXT4 partition.

---

### Post by oldfred on 2012-12-05
Dynamic for Windows is like LVM is for Linux. It is a logical partition overlay to the physical partitions. As such Linux tools will not modify or mount the dynamic partitions. 
If you left space you may be able to force Linux into another partition,but could never boot Windows from grub as it cannot 'see' the dynamic partition to boot from.

---

### Post by darkod on 2012-12-05
As far as I know, the Dynamic refers to the whole disk, not only the specific partitions. That's where the problem lies.

If it was only the partitions, logic would say you can use unpartitioned space for ubuntu without problems.

But if the disk is Dynamic, that includes the unpartitioned space.

In Disk Management, if you look at the left center of the screen, it should say like:
Disk 0
Dynamic

or:
Disk 0
Basic

The disk is basic or dynamic, not the partitions. And if it's dynamic, you can't use it from linux the same way as windows doesn't understand not only linux LVM but linux partitions in general.

---

### Post by Brando569 on 2012-12-15
Yep, I just looked and the whole disk is dynamic. This makes complete sense no, thanks! I'm going to try to convert it and hope all goes well!

---

### Post by Brando569 on 2012-12-16
So I converted the disk from Dynamic to Basic (it took 4 hours!) and Kubuntu installed but installing Grub to the MBR *still* failed! What's going on here??

> kubuntu@kubuntu:~$ sudo grub-install /dev/sda
Path `/boot/grub' is not readable by GRUB on boot. Installation is impossible. Aborting.

kubuntu@kubuntu:~$ sudo grub-install /dev/sda4
Path `/boot/grub' is not readable by GRUB on boot. Installation is impossible. Aborting.

I also can't post anything from boot-repair because I can't get it installed

> kubuntu@kubuntu:~$ sudo apt-get install boot-repair 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 boot-repair : Depends: boot-sav (>= 3.196) but 3.196~ppa3~quantal is to be installed
E: Unable to correct problems, you have held broken packages.

Here's the partition table
> ubuntu@kubuntu:~$ sudo fdisk /dev/sda

Command (m for help): p

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xf4aea3a7

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      409599      203776    7  HPFS/NTFS/exFAT
/dev/sda2          409600   843814911   421702656    7  HPFS/NTFS/exFAT
/dev/sda3       946214910   976771119    15278105    f  W95 Ext'd (LBA)
/dev/sda4       843814912   946212863    51198976   83  Linux
/dev/sda5       946214912   976560127    15172608    7  HPFS/NTFS/exFAT
/dev/sda6       976560192   976771119      105464    b  W95 FAT32

Partition table entries are not in disk order

[img]http://img809.imageshack.us/img809/1906/snapshot1nb.png[/img]

---

### Post by oldfred on 2012-12-16
In the Boot-Repair thread is another users with issues, I think it is being worked on.

You can try manual install of grub, but if it cannot read /boot/grub, did it install correctly? Or does partition have issues.

We also have seen some issues with some systems where if boot files are beyond 100GB on drive grub may have issues finding its files. 
Have you turned fast boot off and have AHCI on in BIOS. Not sure if any other settings may be required.

---

### Post by Brando569 on 2012-12-16
The partition itself is fine, it mounts perfectly and fsck.ext4 reports that it is clean. There aren't any options for fastboot or AHCI in the BIOS so I can't toggle those. 

By installing grub manually do you mean this? Because that's what I've been doing and it fails.
> kubuntu@kubuntu:~$ sudo modprobe dm-mod
kubuntu@kubuntu:~$ sudo grub-install --target=i386-pc --recheck  /dev/sda

I really don't want to move a 400 GB partition unless I absolutely have to because it will take another few hours :-/

---

### Post by YannBuntu on 2012-12-16
> **Brando569 said:**
> I also can't post anything from boot-repair because I can't get it installed

[https://bugs.launchpad.net/boot-repair/+bug/1090841](https://bugs.launchpad.net/boot-repair/+bug/1090841)
please retry when all packages are ready on the PPA: [https://launchpad.net/~yannubuntu/+archive/boot-repair/+packages](https://launchpad.net/~yannubuntu/+archive/boot-repair/+packages)

---

### Post by darkod on 2012-12-17
No, I think he meant a full reinstall of the grub packages. That command only adds/restores grub2 to the MBR but if the package itself didn't install detecting the Dynamic disk, having grub2 on the MBR won't do you any good.

I would use the chroot procedure from live mode to get grub2 completely purged and reinstalled. I have one post bookmarked. Note that your root is /dev/sda4 so in the very first command you will have to mount that partition instead of /dev/sdb5 like in the example:
[http://ubuntuforums.org/showpost.php?p=11858371&postcount=29](http://ubuntuforums.org/showpost.php?p=11858371&postcount=29)

PS EDIT. There is also one command that needs to be changed in that link. It's in the second block of commands, the grub-install should be to /dev/sda, not /dev/sdb. With the above mentioned mount command, those are the two that you need to change depending on your setup.

---

### Post by Brando569 on 2012-12-17
Thanks, I'll give it a try when I'm at her place again this Friday. I've never had so many problems installing a "noob friendly" Linux distribution, the problems I've been having are turning my girlfriend away from ever using Linux in the first place. I told her that I've had less problems installing Arch Linux (which for those of you that don't know, is a manual installation which has to be configured by hand, no installer is present)which takes about 4-8 hours :-/

---

