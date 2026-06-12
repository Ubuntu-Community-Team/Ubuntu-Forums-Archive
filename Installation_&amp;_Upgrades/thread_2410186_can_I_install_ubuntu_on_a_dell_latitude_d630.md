---
title: "can I install ubuntu on a dell latitude d630?"
date: 2019-01-12
forum: Installation &amp; Upgrades
---

### Post by iamtheeggman2 on 2019-01-12
Hi I am looking for a recommendation as to whether I should try installing ubuntu or another linux distro onto a dell latitude 630 laptop. This is an intel core 2 duo device. I am concerned as its running xp which is a very outdated software, but i don't want to install a later copy of windows because windows is a very big programme and this is not a new laptop... thanks in advance.

I tried running a few live disks of various distros but found it didn't work out so well.

---

### Post by TheFu on 2019-01-12
Should be fine for Xubuntu, Lubuntu or one of the lighter variants.  I would avoid the heavier Ubuntu versions running KDE, Gnome3.  The main issue is how heavy the GUI/Desktop is.  Stay with light versions and it should be fine.

Live disks will be much slower because Flash storage and DVDs are slow.  Also, they need enough RAM to hold anything installed during the session.

Don't expect a D630 to be blazing fast, but it is more than sufficient for an ok desktop, assuming it has sufficient RAM.

---

### Post by iamtheeggman2 on 2019-01-13
Curiously linux puppy loaded up alright but what I really wanted to do was attach a large usb device to it and copy off a lot of files onto it from the laptop, however, the file-manager for some weird reason would only let you select/highlight one file at a time. for some reason the laptop has usb drivers which read usb sticks but the large western digital drive wasn't readable, even though the computer bleeped in windows xp, it just wouldn't read it. there was a problem device found in the windows setup for hardware and it said the usb was not installed, however, upon going to dells site it had smart drive usb drivers but not one for the outstanding usb item. furthermore the windows installation appears to have issues with wifi in that although the dell software is available, even though it installed ok, with no error messages, the wifi adapter still wouldn't show as installed s0 i couldn't ask it to simply find software from Microsoft and then download.

Curiously I just discovered why windows xp on the laptop wouldnt see the hard disk, it says it has a GPT protected filesystem

Here is an article explaining osme of it. However I am curious , I am pretty sure linux was used to create the fat32 partition, it didn't say anything about what style of file system it was writing, i had just assumed all windows would see it.Is linux still good for writing an NTFS file system? If I can do that then I can simply convert it all and then it will be accessible to my windows laptop.

[https://www.easeus.com/partition-master/access-gpt-protective-partition-without-losing-data.html](https://www.easeus.com/partition-master/access-gpt-protective-partition-without-losing-data.html)

---

### Post by TheFu on 2019-01-13
I would guess that the disk is failing based on your description.  Make multiple backups of the data you need now, before it is too late.  This assumes it isn't already too late.  When 2 OSes cannot access a disk, that isn't a good sign.

Try using a different USB port, a different USB cable, and if you can, pull the physical HDD from the enclosure and try a different USB enclosure.  But first, get all the data you can off the current device.  All storage fails and it is never at a convenient time.

Puppy linux is good for quick looks at data, but not-so-good for a desktop system due to poor, really poor, security choices.

BTW, GPT doesn't mean what you think it means.  It is just a different type of partition table.  I think WinXP needs drivers loaded to access it, but it has been so long I don't remember exactly.  Any Linux distro since 2010 or so can access GPT just fine.  GPT was created to deal with really large HDDs and is required to use HDDs over 2TB in size. It doesn't have a 4 partition limitation like MBR partitioned disk do and the 2 copies of the partition table is written at opposite ends of the disk, unlike MBR partition tables which are only written at the beginning of the disk.  

The wikipedia article on GPT is pretty good if you want to understand more.  GPT is a good thing.

Linux prefers native Linux file systems over others, but it can create, read, and write NTFS, FAT16, FAT32 and exFAT partitions if required.  I think exFAT requires added tools to the Linux install. Actually, all of them probably do, but that is just an apt-get away. Not a big deal, unless you are running Linux from optical storage or a read-only flash drive.

---

### Post by iamtheeggman2 on 2019-01-13
The disk isnt failing, it is read perfectly fine by linux, the problem is the laptop wont read that type of filesysem as per the link i put on there to describe the issue.

I think best option is to simply replace the hdd fat32 with ntfs and then all should be fie next time i want to access the usb disk on the laptop.

Thanks for the response.

---

### Post by TheFu on 2019-01-13
If it is GPT, then XP will only use the backwards compatible part of GPT that makes it appear as an MBR. This only works partially. GPT doesn't support "logical" partitions, only primary partitions.  
[https://docs.microsoft.com/en-us/windows-hardware/manufacture/desktop/windows-and-gpt-faq](https://docs.microsoft.com/en-us/windows-hardware/manufacture/desktop/windows-and-gpt-faq)
> Windows XP and the original release of Windows Server 2003 have a limit of 2TB per physical disk, including all partitions.

There is no real limit for the number of partitions that GPT supports, they are all primary.  However, the MSFT implementation chose to allow only 127 partitions.  Today, that doesn't seem like any limitation.  I've never used more than 60 myself.

How large is the disk? Is the partition to be accessed wholly within the first 2 TB?

But you are staring at the issue and NTFS is definitely better for non-flash disks than FAT32.  FAT32 is the best choice when the primary goal is wide support across as many devices as possible - cameras, video systems, phones, tablets, computers, IoT stuff, etc.

---

### Post by oldfred on 2019-01-13
Is drive connected internally or externally.

I had a core2 duo system with XP on one drive and then installed Ubuntu on the other drive. 
Later learned about advantages of gpt and got a tiny SSD (60GB) but then recommendation was to use gpt.
But system was set for IDE for drives, and you have to have AHCI for trim to work. I dual booted only for a very short time as had to change BIOS settings to IDE to boot XP and it took 3 minutes to boot and wanted multiple updates & reboots. 

Check what setting your BIOS has for drive, if IDE it may be part of the issue.
But if a very large drive, some older BIOS will not support it.

---

### Post by iamtheeggman2 on 2019-01-13
usb drive is only 500gb but that is beyond the 32gb limit set in  windows, which i read, was deliberate to make people go to ntfs. 

i  have tried resizing the drive with gparted and to make a new partition  with ntfs, it failed to do this and wanted to resize the shrunken fat32  to the entire disk again, i am now trying to do this one step at a time,  to shrink my partition of fat32 down to the smallest i can with the  data on it and then make a new ntfs one in the new freee space. then if  successful, i can copy the data fom the fat32 partition into the ntfs  one.

---

