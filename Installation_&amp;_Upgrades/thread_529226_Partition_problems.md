---
title: "Partition problems"
date: 2007-08-18
forum: Installation &amp; Upgrades
---

### Post by t2000kw on 2007-08-18
I have a few problems that are preventing me from installing Ubuntu on a laptop PC. THis is not a laptop problem per se, it just happens to be a laptop this has happened on.

I have resized the Windows 98 partition a few times trying out different Linux and BSD OS's and to get back the master boot record I did the FDISK /MBR command and got my Windows boot back to normal. As far as Windows is concerned, and Partition Magic also, everything is fine with the Windows partition.

When I want to make new partitions I can create them with Partition Magic from within Windows, and I can format the swap partition. PM gets stuck trying to format the third partition on the disk (3 partitions total) as EXT2 (this is an old PM program, ver. 4, so it doesn't support EXT3 yet). My plan was to let Gparted format these partitions anyway.

Well, when I have tried to install Dapper or Edgy, when I get to the part where you tell it which partitions to use for /, /swap, etc., I want to choose only two, no more, one for / and one for /swap. After I set /swap for /hda2 and / for hda3 (hda1 would be for Windows), it wants me to pick another item and give it a partition. That should be an option, not a mandatory thing, and I can't click on NEXT as it is grayed out. So I'm stuck.

Additional information, though, that might be helpful:

1. Using a Gparted live CD, I can see the disk but it doesn't recognize that I have three partitions, or that Windows is installed on any of the disk. 

2. Using a Knoppix live CD and QTParted, I have the same problem, and this partition manager has been better at working with Windows partitions than Gparted has. 

I don't have a convenient way to back up my laptop drive windows partition, though I can see it over the home network. I can back up the directories but not the full disk in an ISO image. I do have a ZIP drive for it and it works (one internal and one external), though these are 100 MB disks and it will take forever to back up the drive that way. I also don't know what software I would use for the backup and restore over that many disks. I have about 3.5 gigs to back up. 

I don't know why Windows will boot but other things can't see it. Is the partition screwed up, and if so, how can I get it fixed, especially if I can do so without destroying Windows in the process.

My ultimate goal it to get a dual boot setup and use Ubuntu, probably exclusively, and over time I will decide to just delete Windows, saving only the files I might need later like documents and such. Then I can have the full 8.3 gigs for Ubuntu.

So, I see a couple of different approaches that someone might be able to help me with. If I can get the installation to continue with using the / and /swap partitions I choose during the install process and go on to the next step, I won't have to do a lot of work. At least the installer recognizes that there are three partitions (must be a newer version of Gparted than the live disk I have). 

Or, a backup and reformat, then a restore of the Windows files, then an installation of Ubuntu.

---

### Post by logos34 on 2007-08-19
Well, you should definitely back up your files.  Not familiar with win98, but isn't there a "network places" you can backup your folders to, then grab those files using another computer on the lan?  Or, since I take it this laptop has only a cdrom (not cd writer), you might consider taking the hard disk out and transferring it to a usb enclosure and then copying over the files to another drive (or cds) on another machine.  

As for the installation problems, you might just want click on hda2 and 3 and select 'delete', then start over and create a swap partition (type='swap') with mountpoint '/swap', then make a root partition (type='ext3', not ext2) on remaining space with mountpoint '/'.  You'll end up with swap on hda2, and root on hda3.  Do NOT tick 'format' box next to windows/hda1.

---

### Post by t2000kw on 2007-08-19
> **logos34 said:**
> Well, you should definitely back up your files.  Not familiar with win98, but isn't there a "network places" you can backup your folders to, then grab those files using another computer on the lan?  Or, since I take it this laptop has only a cdrom (not cd writer), you might consider taking the hard disk out and transferring it to a usb enclosure and then copying over the files to another drive (or cds) on another machine.  

This is an older drive. I have a laptop drive IDE to regular IDE drive adapter and it didn't work (the hookup for the LT drive is different than the more recent ones, apparently). I was going to create a drive image of the LT drive on a separate partition on my desktop computer. 

 I might end up buying a USB DVD/CD-R/RW and backing things up that way. It's more useful than making an enclosure for the LT drive that won't be of much use after that, and there's still the unsolved problem of connector compatibility. It might be a proprietary Dell thing, I don't know). . I might have to wait to do this, or I might just back up the rest o my files over the network by a manual copy and see how that goes, then reformat and reinstall Windows, then copy everything that will copy back to the LT drive. 

It's a thought, so thanks for the suggestion. It might be the only one that works--starting over after a backup. 

> **logos34 said:**
> As for the installation problems, you might just want click on hda2 and 3 and select 'delete', then start over and create a swap partition (type='swap') with mountpoint '/swap', then make a root partition (type='ext3', not ext2) on remaining space with mountpoint '/'.  You'll end up with swap on hda2, and root on hda3.  Do NOT tick 'format' box next to windows/hda1.

I have deleted these before and recreated them. Unfortunately, the Gparted and QTparted I have don't "see" these partitions except for the one in the Ubuntu installer. WHen run form the live CD as a standalone program they don't allow me to see the partitions. It just shows one big 8+ GB of unallocated space. 

I Do have the option of using the whole disk, of course. Not exactly what I wanted, but it might be what I do if I don't get an external DVD drive to write to with a backup first (I would back up my files over the network--as many as possible--first, though). .

---

### Post by t2000kw on 2007-08-21
Update--backed up the system over the home network onto a DVD. Then repartitioned and installed Dapper. 

Now I need to figure out how to make a startup script for the touchpad configuration program I installed since it won't work after Xwindows starts. I don't have the knowledge yet for this part but will be learning about scripts soon. But one mild bump and I'm typing somewhere else on the screen. Maybe I should post this part in another forum but here is info about the open source touchpad driver I'm planning on using.

[http://www.compass.com/synaptics/](http://www.compass.com/synaptics/)

[http://www.compass.com/tpconfig/touchpad](http://www.compass.com/tpconfig/touchpad)

---

