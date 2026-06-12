---
title: "Laptop partition table review needed"
date: 2007-03-27
forum: Installation &amp; Upgrades
---

### Post by mxwl on 2007-03-27
Please review my partition table below.  My first Linux experience was Dapper Drake dual boot on my desktop.  The install was plagued with GRUB & MBR issues I would like to avoid this time.

Goal
- to install Ubuntu 6.10 in a dual boot setup with XP Pro SP2

Hardware
- 5 year old Toshiba laptop
- newer 100gb+ drive
- partitions previously set up (correctly???)

Partitions
- /dev/hda1 ntfs 50gb boot (xp pro sp2 installed)
- /dev/hda2 fat32 30gb lba
- /dev/hda3 linux-swap 2gb
- /dev/hda4 ext3 30gb

My Questions
- 1. Do my partitions appear to be set up properly?
- 2. Do I need an ext2 boot partition?
- 3. Do my partitions need to be rearranged to the following order - ntfs, ext3, linux-swap, fat32?  Or resized?
- 4. How can I avoid the GRUB prompt after install?  I'm afraid of causing problems with my MBR?
- 5. I read I need to make ext3 a primary partition.  How?  I have GParted.

I'm a newbie so please keep that in mind.  I have SystemRestoreCD-x86-0.3.4 ready to go in case of emergency - but I'd prefer to eliminate mistakes prior to installation.

Thanks for your help.

Maxwell

---

### Post by mardawi on 2007-03-27
I've just installed ubuntu 6.10 dual boot successfully after facing some problems with gparted, maybe my experience could be useful to you
[http://ubuntuforums.org/showthread.php?t=392533](http://ubuntuforums.org/showthread.php?t=392533)

My answers to your questions:

- 1. Do my partitions appear to be set up properly?
I wouldn't do that if i were you; i would keep my root ext3 partition after the ntfs directly and my swap partition at the end. I wouldn't use fat32 at all. I would keep all the partitions primary.

- 2. Do I need an ext2 boot partition?
No, i don't think so.
- 3. Do my partitions need to be rearranged to the following order - ntfs, ext3, linux-swap, fat32? Or resized?
Here is what i would do
ntfs 50 gb
ext3 15 gb
ext3 45 gb
swap 2gb

when installing ubuntu, choose to manually configure partitions, this will launch gparted, delete all the partitions and just keep your ntfs partition, create the new partitions as shown above.
click next and the installation will ask you how to mount the partitions, make it to look like this:
/media/hda1   50gb   partition #1   [not checked for formating]
/                     15gb   partition #2   [checked for formating]
/home            45gb   partition #3   [checked for formating]
swap              2gb     partition #4   [checked for formating]

I believe you were going to use the fat32 partition for share files between ubuntu and windows, there are some free programs that you can install in windows to mount ext3 partition, so you can use the /home partition for sharing files and save yourself the headache of using a 3rd format.


- 4. How can I avoid the GRUB prompt after install? I'm afraid of causing problems with my MBR?
I wouldn't worry about that, if GRUB causes any problems it can be either reinstalled or over--written by windows by booting form the windows installation CD and going to the recovery command line and using fixboot or fixmbr commands.

- 5. I read I need to make ext3 a primary partition. How? I have GParted.
by deleting all the logical partitions in the extended partition, deleting the extended partition, and recreating them using GParted.

What did you use to create these partitions in the first place?

Good luck!

---

### Post by mxwl on 2007-03-27
Thanks for the input.

I used GParted to install the partitions when I attempted to install an apparently bad ISO of Dapper Drake a few months ago.  I'm now using a good ISO of Edgy Eft.  You are correct about the FAT32 partition.  I want to share files between Edgy Eft & XP.

Can I ask, why you recommend having two ext3 partitions?  I assume the first 15GB ext3 partition is for the OS, the second 45GB is for my apps & files?  Do I need lba on the root partition?  I read I may need it since the MBR can only read to cylinder 1024 on the drive.

I appreciate your help.  Glad to hear yours is up and running.

---

### Post by mardawi on 2007-03-28
I use two partitions of ext3 myself, the first smaller one for root system files and the larger one for my files and programs which i mount in windows to share files between ubuntu and windows. i keep my root partitions away from windows so it doesn't miss with it ;)

I've read that grub had problems in the past in loading the kernel if it wasn't in the first 8 gb, but i currently have my root partition after the 12 gb ntfs partition and it works well for me. i'm not really sure about the lba label though... i thought it was for the extended partition! maybe it would be a good idea to wait for others with more experience to comment on this.

---

