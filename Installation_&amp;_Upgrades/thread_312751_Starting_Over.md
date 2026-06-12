---
title: "Starting Over"
date: 2006-12-04
forum: Installation &amp; Upgrades
---

### Post by coldstatue on 2006-12-04
Ok, I had some problems with trying to install on a second drive, and endless GRUB errors. So, because I'd like to actually try this OS out, I'm taking a different route. I would like some advice on partitions, but let me tell you what I'm going to do.

I ordered a new HD, and I will ghost a copy of my Win drive to it for safety.

Then, I will partition my primary drive, and just install Linux, dual-boot, on that. I am starting with my existing Windows setup, and want to keep it as it is. 

I will be using Partition Magic to prepare the drive before installing Linux. I know many will disagree with me here, but I've had lots of problems thus far, and would like a friendly Windows environment to work on something so foreign to me.

I've got PLENTY of space, so that's not even an issue, I will dedicate plenty to the Linux Partitions.

I have 150 GB total. I have 120 Used up with my Windows stuff. (some will be deleted, I have plenty of space in there.)

30 Will be for Linux. 

So, here are my questions.

How many partitions will I need?
I know I need root and swap. But that swap isn't the one that can swap with Windows, is it? It's like a virtual RAM kind of swap, right?

What type should each one be? ext2, 3? 

What about size?

Basically, as I understand it, I need a root for all the linux files, a swap for like a virtual RAM partition (?) and a "share" partition for Win/Linux. 

So please tell me in very simple terms about the best sizing, and type of partitions I need.

Also, when installing Ubuntu Edgy Eft, will it just know to install into my MBR? I want it to... I think. I had too many problems trying to let the install figure things out on its own, so I want to be sure I tell it what to do. I will be using Boot Magic for my boot menu, because GRUB and Lilo completely destroyed my faith in messing with a Windows boot from software that comes from a Linux community. I know, I know. But I've seen so many GRUB errors, I can't list them all. I'm just sick of reading about something I have no interest in. I just want to try "The Linux for human beings."

I have no idea what I'm doing, but I will have a back-up of my entire drive.

Thanks for any help. And please, talk to me like a new-born, because when it comes to Linux, I am.

---

### Post by veli on 2006-12-04
An example for partition scheme would be:
First, instead of Partition Magic, download Simply Mepis Live CD. it has Qtparted partition program you can safely use to partition the drive (shrinking and creating partitions is very easy, just dragging and right clicks). But if you wish, just use PM.
1. So, you install Windows onto the 150 Gb HDD - done
2. You need to shrink the Windows partition to 120 GB.
3. In the free 30 GB space you could do many things, I'd do the following:

I created a logical (extended) partition first. After that I created SWAP partition for Linux (it's not for Windows) - 512 MB would be enough. And finally, the rest of the free space-use ext3 file system for Linux root.

When installing Ubuntu, go through manual partitioning in the installer, and select the right partitions, / for root.

Also, you could just select the option given you by the installer to use the free space, but I prefer to use the manual one.

If you want to write on the NTFS partition, you'll have to install some tools for that, or you could compile your own kernel enabling the NTFS write support. 

Another partition scheme would be:

1. Install Windows onto the 150 GB (NTFS, or FAT32 if XP allows you).
2. Shrink it to saying 50 GB (or more, or less, it depends on how many programs you'll install).
3. Create the logical partition from the freed 100 GB space.
3. Create SWAP-512 MB.
4. Create Linux root partition: journaled ext3 file system, saying 20 GB (or less, or more, depending on how many programs you'll need)
5. The rest of the free space dedicate to a shared partition: FAT32. This is for your movies, pictures, docs, MP3 etc. You'll be able to read/write on this partition from both Linux/Windows with no problems at all.

Ext3 file system is the most stable and well tested. You can tweaked it for best performance. I myself use reiserfs at the moment, and I don't have any complaints. 

Do not fill the root file system to the top. I prefer the root partition to be at least 50% free.

If you decide to use QtParted for partitioning, just ask, I'll give you directions, I'll selct the instant notification to this thread.

Hope this helps.

---

### Post by coldstatue on 2006-12-05
Ok, Please confirm if I have this correct.

I have a windows partition of 150 GB
I will resize it to 120GB.
Then I create a logical partition, in the 30 free GB, and within that:
I will create 3 partitions in the free space.
20 GB for root, with ext3 file system.
1 GB for swap, with ext3 3file system
9 GB for share, with FAT32 file system - to be read by both OSs.

Is this correct? Please check that I have the file systems right, as this bit was a little unclear to me.

This is all pretty confusing stuff for me, so I want to be sure I have laid out a verified plan before I start.

Also, Should I install Boot Magic before or after ubuntu? Because I'm using Boot Magic, I guess it doesn't matter if the boot files are within the first 2 GB. So, will the ubuntu install allow me to determine where they go?

Thanks again.

---

### Post by veli on 2006-12-05
Ok, it's almost correct.
IMO, you don't need to create FAT32 partition in this case, because  Linux will be able to read the files from the Windows partition. But if you want to write to the Win partition, you'll need to investigate how to enable NTFS write support. I don't use NTFS write support 'cause my documents are in a FAT32 partition. 

Just in the logical partition create only SWAP (1GB) and 29GB for /root (ext3). The file system for SWAP is NOT ext3. It's "Linux SWAP" or something like that, can't remember now.

Also, you don't need to install any boot loaders, Ubuntu will install the GRUB loader on the Master Boot record (MBR). When you reboot, your Windows will be the last option and you can start it by moving to it with the arrows and press Enter. You could make your Windows the first option if you wish. If you want to get rid of the other OS, deleting the Linux partition will not delete the GRUB though. You'll need the Windows installation CD. boot with it, get to the recovery console, and type fixmbr to restore the MBR. I've done this many times.

So, create the partitions first and then during Ubuntu installation select "manual partitioning", and then assign the correct partitions for swap and /root. You'll see the partitions like hda?, or sda?, and you can orientate which one is the root ( or SWAP) by their size. This is a pretty straightforward process.

This partition scheme was the first to try over a year ago, it worked for me, but I was using Linux more and more, and I had to start over. I shrank the Windows, now Linux and Windows have the same size, and the rest is FAT32 for files.

---

### Post by coldstatue on 2006-12-05
So if I do want to create a separate sharing partition, and I wanted both XP and Ubuntu to read/write to/from it, it would need to be NTFS??

---

### Post by bulldog on 2006-12-05
Nope never use NTFS for a share partition.
You stated you have two drives.
Why installing ubuntu on your windows disk?
I should put it on his own separate disk so your windows is safe :D 

To partition just download the gparted live cd ,it's like PM but is much better to handle your partitions.
It's 25MB,burn it to a cd-r and boot from it.

[http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828)

Now you have to choose the right disk to manage,you can tell by it's partitions which you should choose.

Let me know what your decision is,I can help you with your dual boot from one disk as well as two.
Only thing is,I exist on using GRUB because it's one of the best boot loaders you can imagine.
The trouble you read on GRUB is mostly ignorance in how it works and where it should be installed,but the configuration is quit easy to do if you get the hang of it.

---

### Post by coldstatue on 2006-12-05
Well, I might go on a second drive, but I'd still want a partition that can be both read by, and written to, by both OSs. What file structure would I use for that?

I am actually leaning more and more to the second drive idea, but I want to make sure I understand the partitioning better before I make any decisions.

Thanks to all for the help.

---

### Post by bulldog on 2006-12-05
Well for the file system for a shared partition you can choose FAT32 or ext3.
There's a little app which,if installed in windows,it can make windows read and write to a ext3 partition.

[http://www.fs-driver.org/](http://www.fs-driver.org/)

But it's your choice,you have to understand,ubuntu can **read** NTFS,but can't **write** to it natively,although there is a driver who makes it possible,but due to a bad experience in the past,I can't recommend this.

The partitioning is really no issue.
You have to read carefully what you're going to change and what to format.
As long as you not hit the apply button,there's nothing changed,and you can back out anytime.

---

### Post by coldstatue on 2006-12-05
ok, so fat32 and ntfs are 2 different things, right?
So if I go the ext3 route, I'll install a driver for windows to read/write it.
And if I go fat32, ubuntu AND windows can read/write to that natively?

And NTFS would require a driver for linux to write to.

Do I have this correct?

Thank you

---

### Post by bulldog on 2006-12-05
Yes,totally :D

---

### Post by coldstatue on 2006-12-05
Excellent. Thanks for all the help. After hours and hours of reading, I was unsure of these things, so I'm very happy to feel a bit more confident about it.

---

### Post by ADT on 2006-12-11
I was reading this thread and noticed that no one said anything about giving grub it's own partition. I have always had grub in it's own 20 Mb partition and then a second partition for root and a third partition for swap. Does grub work perfectly fine if it is installed on the same partition as the root file system ie grub and root on 1st partition, swap on 2nd partition.

---

### Post by bulldog on 2006-12-11
GRUB is located in the MBR of a hard disk.
Think you mean a /boot partition.
This can be done,in fact you can make as many partitions as you like /var,or /etc and so on.

But this is for the more experienced users who do this with a special purpose.

So anyone can install GRUB into the MBR and the menu.lst is located at /boot/grub/menu.lst if you want to change something.

---

### Post by ADT on 2006-12-12
Thanks, I should have wrote /boot partition.
I read that a /boot partition is used to store an image of your kernel so that if something happens to your /root partition's kernel you can use the  /boot partition to reinstall the kernel on /root without needing to go through the kernel configuration and compilation stages. I think /boot also has a copy of grub files aswell.
So /boot is used as a backup for important system files like grub and the kernel.

---

### Post by bulldog on 2006-12-12
Boot is the partition which contain the kernel versions and GRUB as well.
Don't know what you mean by 'a copy',as far as I know is the only kernel version located on /boot.

Normally is /boot a directory under the / but if you make a separate /boot,you won't have an extra /boot under / as far as I know.

---

### Post by ADT on 2006-12-12
I don't know what exactly is stored in /boot I was just making assumptions.
In my previous install of ubuntu there was a /boot directory in my root partition even though I had a seperate /boot partition. 
I installed xubuntu today and just setup three partitions, root, home and swap. Thanks for explaining that I don't need a /boot partition, I always thought it was needed.

---

