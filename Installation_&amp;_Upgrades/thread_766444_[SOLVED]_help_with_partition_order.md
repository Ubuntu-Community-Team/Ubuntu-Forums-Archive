---
title: "[SOLVED] help with partition order"
date: 2008-04-25
forum: Installation &amp; Upgrades
---

### Post by soumo on 2008-04-25
Hi all, 
I've decided to do a fresh install of hardy on my 120 GB laptop of which there is currently a 6GB service partition (Lenovo recovery), followed by Vista.

My plan is to wipe the service partition, I've already shrunk Vista and will add the savings to the old service partition.

I then want 3 new partitions, 1 ext 3 for Hardy 8.10, 1 linux swap of 2GB (I have 2GB RAM), and finally a joint storage partition accessible by Vista and Ubuntu. 

I would like to know:
(a) What is the best order for the 4 partitions, (I've read Vista should come first?)

(b) Recommended sizes?

(c) What type of partition the joint storage one should be?  I previously had issues with an external usb drive that was formatted as fat32.  I was unable to easily transfer files from linux (gutsy) that had characters in the name such as : or \ without first renaming them.  I also don't want to get stuck by the 4GB limit in NTFS.

Can some one sort of point out what the final order and types should be?

-Very appreciated.

---

### Post by rimoth on 2008-04-25
Hi,

If you wipe the service partition I guess you are kissing goodbye to the MS Windows software. Not a problem for you as I can guess you're happy with Ubuntu but may affect the resale value of the laptop. 

For Vista why not run it through parallels or VM Ware. 

As for the order of the partitions, I was googling this hence arrived at your post. I don't think this matters - which part of the disk do you want to wear out first?

---

### Post by soumo on 2008-04-26
Hi rimoth, thanks for the quick reply.

Actually I will be running Vista as well!  The service partition is a recovery partition that is used to restore the system back to factory status in the event of total system failure.  It is hardwired into Lenovo laptops with an actual recovery key.  As I have the recovery disks, wiping it out frees up 5-6GBs yet poses no real risk...

---

### Post by Lantesh on 2008-04-26
Ok first NTFS does not have a 4GB file size limit.  Fat32 has the limit.  So I would recommend using NTFS as your common storage partition.

As you stated I would put Vista on the first partion, NTFS obviously.  Ubuntu would go on your second partition.  I'd say 25 or 30 gigs is a nice number.  That's typically what use.  Next put your swap file, and finally your common storage partition.  Anyway this is just my opinion on what makes sense to me.  Take it with a grain of salt.

---

### Post by Lord Landis on 2008-04-26
I agree with Lantesh for the most part, but would advise a slightly different approach.

Instead of a 20-30 Gig partition for Ubuntu and the remaining (minus swap) for the joint storage, I'd do one of two things:

1) Set the ubuntu partition to closer to 10-15 Gigs and create a separate partition for /home that holds the other 15-20 Gigs.  This way you'd have five partitions: 
   a - Windows / NTFS
   b - Ubuntu / Ext3
   c - Ubuntu '/home' / Ext3
   d - Ubuntu 'swap' / swap
   e - Shared storage / Fat32
  I say this because I always try to keep /home in a separate partition.  Of course, I also tend to keep /home on a different physical disc, but that's not an option here.

2) Proceed as recommended previously, but when you create your 'shared storage' partition, either mount it as /home during the Ubuntu install, or symlink it in your actual /home directory.  This way you can use all of that space for whatever you need and can easily access files from both OSes.  While this seems a tad complicated to configure, it's going to be more efficient once everything is up and running.

And yes, the Vista partition should be first.

---

### Post by TheMemphisExperience on 2008-04-26
> **Lord Landis said:**
> I agree with Lantesh for the most part, but would advise a slightly different approach.

Instead of a 20-30 Gig partition for Ubuntu and the remaining (minus swap) for the joint storage, I'd do one of two things:

1) Set the ubuntu partition to closer to 10-15 Gigs and create a separate partition for /home that holds the other 15-20 Gigs.  This way you'd have five partitions: 
   a - Windows / NTFS
   b - Ubuntu / Ext3
   c - Ubuntu '/home' / Ext3
   d - Ubuntu 'swap' / swap
   e - Shared storage / Fat32
  I say this because I always try to keep /home in a separate partition.  Of course, I also tend to keep /home on a different physical disc, but that's not an option here.

2) Proceed as recommended previously, but when you create your 'shared storage' partition, either mount it as /home during the Ubuntu install, or symlink it in your actual /home directory.  This way you can use all of that space for whatever you need and can easily access files from both OSes.  While this seems a tad complicated to configure, it's going to be more efficient once everything is up and running.

And yes, the Vista partition should be first.

What is the purpose of the separate home folder?

---

### Post by Lord Landis on 2008-04-26
> **TheMemphisExperience said:**
> What is the purpose of the separate home folder?

It's two-fold.  Primarily it's to keep everything (your data, program settings, and all other 'personal' options) safely sequestered away in the event that you need to reinstall.  By moving it to a separate partition, you don't have to worry about blasting it away w/o first having backed some crucial data up.  Don't get me wrong - you should always backup before a reinstall, but I know I'm guilty of having forgotten a file or three in the process before.

Secondly, and this is more true if it's an actual separate volume instead of just a partition, it *can* increase performance.  Though this is probably mostly subjective and irrelevant with today's disk throughputs, it's still something to consider.

---

### Post by Lantesh on 2008-04-26
> **TheMemphisExperience said:**
> What is the purpose of the separate home folder?

Lord Landis made some good points in his reply to your question here, but I am going to play devils advocate and take a slightly different approach.  I leave the /home folder exactly where Linux puts it, however I DO NOT store my data in it.  All my documents, videos, and any other personal stuff is all kept on another separate drive in it's own logical and organized folders.  I also regularly backup config files like menu.lst, sources.list and others to this drive, but I let Linux keep all the settings stuff in /home.  Now you might ask why would I do this.  It's simple, because I don't want all that configuration stuff mixed in with my documents.  When I reformat and do a clean install that's exactly what I want it to be.  Sure it takes a bit longer getting everything setup again, but this way I know it's fresh, and I don't have any old files hanging around from my last install.

---

### Post by ssican on 2008-04-27
REFERENCES FOR PARTITIONING FOR LINUX:

1) HELP ON PARTITIONING:
[http://www.users.bigpond.net.au/hermanzone/p17.htm#help_on_partitioning](http://www.users.bigpond.net.au/hermanzone/p17.htm#help_on_partitioning)

2) _Primary, Extended, and Logical partitions_.

_Primary partitions_: The original partitioning scheme for PC hard disks allowed only four partitions, thus you are allowed up to 4 primary partitions. **Linux numbers primary partitions 1-4**.

Note: Some OSs (Windows, BSD) can ONLY be installed into a PRIMARY partition.

Linux (and swap) can be installed into a primary or logical partition.

_Extended and Logical partitions_: 
To overcome this limitation, extended partitions are used. A single primary partition may "converted" into an "extended" partition which is then further divided into sub-partitions called logical partitions. Sorry you may not convert more then 1 primary partition into an extended partition. You then create logical partitions within the extended partition. It may be possible to create further extended partitions within an extended partition, although this becomes complicated and I am not sure of any advantage this offers.

**Linux numbers Logical partitions starting with 5: The numbers 1,2,3 and 4 are reserved for the primaries, even if you have just one primary partition**. So if you make one primary partition and one extended extended partition with one logical partition:

The primary would be hda1
The entire extended partition (and any logical partition(s) it contains) would be hda2.
The logical partition within the extended partition would be hda5.
Source:Partitioning Basics(bodhi.zazen)[http://ubuntuforums.org/showthread.php?t=282018](http://ubuntuforums.org/showthread.php?t=282018)

**Partitioning Planning for Linux**:
[http://aplawrence.com/Linux/linux_partitioning.html](http://aplawrence.com/Linux/linux_partitioning.html)

3) **PARTITIONING BASICS**
[http://ubuntuforums.org/showthread.php?t=282018](http://ubuntuforums.org/showthread.php?t=282018)

EDIT:
ANOTHER REFERENCE:

4)HERMAN: [http://users.bigpond.net.au/hermanzone/p3.htm](http://users.bigpond.net.au/hermanzone/p3.htm)
-fig 35      
"This time I'm telling the partitioner that this partition will be a 'Logical' partition.
**The Ubuntu installer's partitioner, 'Partman', will  _silently_ _create an 'Extended' partition_ and make the new logical partition inside it**".

- fig 28      
"I need to tell the partitioner if this partition will be a 'Primary' partition or a logical partition."

"A 'Primary' partition is a partition that will be listed in one of the four spaces in the partition table in the hard disk's Master Boot Record. We only have room there for four entries."

"A 'Logical' partition can be made if we make one of the four entries in the Master Boot Record into **_a special 'extended_' _partition_. _The Ubuntu installer's partitioner, 'Partman', will do this automatically if we select 'Logical_'.**"

"Inside the 'Extended' partition we can create quite a large number of 'logical' partitions. The main condition is, these are in a series or 'contiguous'. There can be a gap between them, but we mustn't seperate the logical partitions by placing any 'primary' partition between two logicals.
That would make any logical partitions on the other side of the interupting primary unuseable."
Source:[http://users.bigpond.net.au/hermanzone/p3.htm](http://users.bigpond.net.au/hermanzone/p3.htm)

---

### Post by Lord Landis on 2008-04-27
> **Lantesh said:**
> It's simple, because I don't want all that configuration stuff mixed in with my documents.  When I reformat and do a clean install that's exactly what I want it to be.  Sure it takes a bit longer getting everything setup again, but this way I know it's fresh, and I don't have any old files hanging around from my last install.

Do you keep *any* of the application config data during a backup/reinstall?  I'd think you'd at least want to hang on to your bookmarks and mail folders, right?  Don't get me wrong - I understand what you're m.o. is, and I think it's pretty smart.  I'd just be miffed if I purged *all* of my configuration data.

Though there is another reason to support your method.  I once installed a new mouse cursor theme from kde-look.org, and it crashed my system.  I don't know how or why, but it completely locked the display - wallpaper gone, icons black, the whole thing.  Of course it was stored in a subdirectory of /home. :lolflag:

---

### Post by Lantesh on 2008-04-27
> **Lord Landis said:**
> Do you keep *any* of the application config data during a backup/reinstall?  I'd think you'd at least want to hang on to your bookmarks and mail folders, right?

I backup my Firefox bookmarks, and my Thunderbird address book about once a week to my storage drive.  I don't worry about the email so much, but even that I do backup prior to a reformat.  Basically I'm pretty good about making regular backups of important stuff.  I even burn the stuff to DVD on a semi regular basis.

---

### Post by soumo on 2008-04-30
Thanks folks,
you have given me a lot of food for thought here.  I will let you know how it all works out.

I am strongly inclined towards Lantesh's suggestion.  I am not so concerned with separate /home as I tar the entire partition to my external drive fairly frequently. I also always seem to have partition issues (see below).  As I understand it, there can be only 4 primary partitions, and I don't want to get into extended stuff until I have enough time to read all the links.

I do think I'd like to have app settings such as bookmarks etc. backed as well, but will do so manually for now...do you guys know if there is a way to take a snapshot of update mgr & synaptic?  The idea would be to know what progs I have installed so that I could build an auto-recovery script without having to go manually re-install after a crash or OS change.  Plus I actually read through each update and decide if it's worth doing or not, and I'd hate to have to redo that.  Do you people typically just accept all?  Lantesh is this what those menu & source files you mentioned were?  I'd be curious to know what exactly you back up?  Could you post a censored script?  No need to explain what the files are as long as I could search them out...?

Lord landis, I was a bit confused by your suggestion:

> 2) Proceed as recommended previously, but when you create your 'shared storage' partition, either mount it as /home during the Ubuntu install, or symlink it in your actual /home directory. This way you can use all of that space for whatever you need and can easily access files from both OSes. While this seems a tad complicated to configure, it's going to be more efficient once everything is up and running.


I am VERY interested in performance increase.  I know you said it was subjective, but can you provide any benchmarks for your system?  I also gather that you meant to skip 1c?  can you re-write 2 as you did 1 with the exact partitions for both symlinked case and not?  I think I used to symlink on Gutsy without issues. I symlinkked to where I stored in Vista.  Any disadvantages, risks?    

All that being said, I currently have other issues to work around.  After resetting my laptop to factory, I shrink Vista, erase the service partition (#1), move Vista left, create the rest of the partitions as per Lantos, and voila!  I have a perfect working Hardy Heron.  The problem now is that Vista is not bootable (though I can full access the Vista partition from heron so I know it's not wiped)!  I think it is the grub or something.  I am wondering if I should leave the service partition, Vista, and unallocated space, add Ubuntu and instead reformat the service partition as the swap 4-5GBs?

-I really appreciate all the help, and am going to take it all in to consideration.  I don't want to have to keep redoing this!

---

### Post by soumo on 2008-04-30
small update:

I've solved the Vista issue according to:
[http://auscoder.com/2007-05-18/restore-vista-mbr-bootloader.html](http://auscoder.com/2007-05-18/restore-vista-mbr-bootloader.html)

Basically, use the Vista startuprecovery tool to fix winload.exe and 'repair' the bootloader.  

So both my systems are up, partitioning is:

/dev/sda2  ntfs        63GB    (Vista) -smallest I could shrink it  
/dev/sda1  ext3        10GB /  (ubu)
/dev/sda3  linux-swap  4GB
/dev/sda4  ntfs        35GB    (storage)

I'm still interested in feedback when you have a chance.

fdisk -l:

>    Device Boot      Start         End      Blocks   Id  System 
/dev/sda2   *           1        8240    66179767    7  HPFS/NTFS
/dev/sda1            8241        9545    76410621   83  Linux
/dev/sda3            9546       10067     4184932   82  Linux swap
/dev/sda4           10068       14593    36347062    7  HPFS/NTFS 


cat /proc/partitions:

> 
major minor  #blocks  name

   8     0  117220824 sda
   8     1   10482412 sda1
   8     2   66187768 sda2
   8     3    4192965 sda3
   8     4   36355095 sda4


/boot/grub/menu.lst:
> 
# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
...
## default num
...
# array will desync and will not let you boot your system.
default		0

## timeout sec
...
## hiddenmenu
...
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below
...
## Setup crashdump menu entries
...
## default grub root device
...

## ## End Default Options ##

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=15bfabe3-bfb7-4bfe-a89b-3822bcb75ef2 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=15bfabe3-bfb7-4bfe-a89b-3822bcb75ef2 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other OS:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Vista (loader)
root		(hd0,1)
savedefault
makeactive
chainloader	+1


---

### Post by Lantesh on 2008-05-02
Well I see you are up and running.  Great!  You asked what config files I backup regularly.  It's not much really.

These config files I backup each time changes are made.
1. sources.list
2. menu.lst
3. fstab
4. xorg.conf

Personal settings
1. Firefox bookmarks
2. Thunderbird address book
3. Thunderbird email folders
4. Liferea feedlist (my RSS reader)

Now of course I have a ton of data on my storage drive.  It is not really possible for me to back all of this up as it is almost 400 gigs of stuff, but I do burn the most important stuff to DVD on a semi-regular basis.  Some people get into some really wild RAID setups, but my PC is a home computer, not some mission critical NASA stuff, so I don't get that involved with backups.

Anyway best of luck with your new setup!

---

