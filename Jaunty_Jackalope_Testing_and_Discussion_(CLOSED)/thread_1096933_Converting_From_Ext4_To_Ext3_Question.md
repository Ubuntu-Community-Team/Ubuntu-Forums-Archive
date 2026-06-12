---
title: "Converting From Ext4 To Ext3 Question"
date: 2009-03-15
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by zerted on 2009-03-15
I'm fed up with data loss on ext4.  Ubuntu completely freezes for me about once every two or three days.  I prefer to leave all my apps open (Firefox, Thunderbird, Sunburd, Xpad, etc...) but I am now losing too much data.  Ubuntu seems most unstable when its total memory usage reaches around 95%.  About 35% program data and rest used by cache (according to the System Monitor panel).  Of course, the problems sometime happen when thats not the case too.

When it crashes, I always lose all my Firefox plugin settings and data.  Yesterday I lost all of my multiple Thunderbird profiles :cry:.  (It looks like the mail files themselves might be fine, but Thunderbird doesn't see them.  Anyone know the fix?)

I want to move back to ext3.  Is it possible for me to copy all my data to an external drive, reformat the existing partition to ext3, and just copy the data back.  I think I would have to edit fstab, but other than that would simply copying everything work ok?  I'd rather not have to reinstall everything again.

---

### Post by asimon on 2009-03-15
Yes, you can do that. Best copy while running from a live CD or something to prevent problems with special block device files. If it's the same parition you should only need to edit the filesystem in /etc/fstab. If you use cp use 'cp -ax /mnt/source/* /mnt/destination/'. 

BTW, I hope this is happening only with Jaunty for you and not with a stable release. I would rather switch distribution than filesystem if it crashes that often.

EDIT: After formatting the UUID of the filesystem changes, thus you may need to update this in /etc/fstab and /boot/grub/menu.lst too if it appears there.

---

### Post by jfernyhough on 2009-03-15
It's easiest to copy and format as you suggested, but really it would be more beneficial to try and isolate the cause of the problem. Are you running with swap space? Do you have an nvidia card? Did you enable compcache to test (which caused crashes for me in high-memory-use situations)?

---

### Post by linuxisevolution on 2009-03-15
If your experiencing data loss with ext4 and you copy your files thats fine, but if you copy the programs settings that are causing your system to freeze you will just have the same experience when you go back to ext3. I would recommended copying your personal files only, and your ~/.mozilla directory. Wipe everything else and start over.

Just a reminder, use the stable file systems, like:

ext2 ,ext3 , jfs, xfs, and reiserfs.

---

### Post by asimon on 2009-03-15
> **linuxisevolution said:**
> Just a reminder, use the stable file systems, like:
We are in the Jaunty subforum. Isn't it our job to use unstable stuff to test it? ;-)

> **linuxisevolution said:**
> ext2 ,ext3 , jfs, xfs, and reiserfs.
As repeated in the current discussions about ext4: xfs has the same problem with data loss after crashes as ext4. Even ext3 has it, but to a much much lesser extent.

---

### Post by linuxisevolution on 2009-03-15
> **asimon said:**
> We are in the Jaunty subforum. Isn't it our job to use unstable stuff to test it? ;-)


As repeated in the current discussions about ext4: xfs has the same problem with data loss after crashes as ext4. Even ext3 has it, but to a much much lesser extent.


I didn't notice we were in this subforum lol. Oh, and thanks for letting me know about xfs before I used it :D


EDIT: I have tried all of those except ext4 and xfs. I have to much critical data to use testing filesystems. I use the older ones... NTFS, EXT3, REISERFS are my main people.

---

### Post by asimon on 2009-03-15
> **linuxisevolution said:**
> I use the older ones... NTFS, EXT3, REISERFS are my main people.
A wise choice. I use ext4 for my system partitions and although I haven't had any problems with it, I will stick to ext3 for my valuable data for at least half a year - minimum.

---

### Post by linuxisevolution on 2009-03-15
> **asimon said:**
> A wise choice. I use ext4 for my system partitions and although I haven't had any problems with it, I will stick to ext3 for my valuable data for at least half a year - minimum.

A half a year? That's all? I noticed your running Kubuntu, is it buggy still?


I am running kde 3.5.X with 290mb of ram on my laptop and it is very fast -surprisingly. (ubuntu hardy)

I run Gnome 2.22.3 on my desktop with 4gb of ram. (Ubuntu hardy)

I also run Gnome 2.22.3 on the family pc with 2gb of ram (Ubuntu Intrepid)

Just a thought...

---

### Post by zerted on 2009-03-15
Good point, I think I should reinstall everything.  Is there a good way to extract the selected programs from Add/Remove Programs?

I have a /, /home, and swap partitions (9.3GB).  I use a X61 Tablet which has embedded Intel graphics and 2GB of system memory.  I keep graphical effects completely disabled, though minimal effects sometimes get reenabled after the crashes.  I use nautilus with addons from Ubuntu-Tweak.  I have a bunch of hard drive space (320GB), so I have tons of programs installed, but I don't use most of them.  I try to keep my wireless disabled (oh, there should be a disconnected icon.  If I'm not connected through wired or wireless and wireless is enabled, its just displays the wireless icon with 0 signal strength).

To be fair, I should point out that my average memory usage is around 30% programs and 60% cache, so being unstable when reaching +95% may not really be that important since its normally so close to it anyway.

Thanks for your quick and helpful replies.

---

### Post by linuxisevolution on 2009-03-15
> **zerted said:**
> Good point, I think I should reinstall everything.  Is there a good way to extract the selected programs from Add/Remove Programs?

I have a /, /home, and swap partitions (9.3GB).  I use a X61 Tablet which has embedded Intel graphics and 2GB of system memory.  I keep graphical effects completely disabled, though minimal effects sometimes get reenabled after the crashes.  I use nautilus with addons from Ubuntu-Tweak.  I have a bunch of hard drive space (320GB), so I have tons of programs installed, but I don't use most of them.  I try to keep my wireless disabled (oh, there should be a disconnected icon.  If I'm not connected through wired or wireless and wireless is enabled, its just displays the wireless icon with 0 signal strength).

To be fair, I should point out that my average memory usage is around 30% programs and 60% cache, so being unstable when reaching +95% may not really be that important since its normally so close to it anyway.

Thanks for your quick and helpful replies.

You should be able to keep your /home. Just do a manual partition during the install and select your /home to be used, JUST DON'T CLICK FORMAT. System settings are stored in /etc , but like I said, no use in reinstalling if your going to use the corrupted settings. All the problems you say can be related to broken packages/file system corruption.

I had the same problem. You COULD boot from a livecd and run fsck on the selected partition to try to repair it. It worked for fixing my windows and Linux Mint install, but I later formatted because Linux Mint sucks IMHO.

---

### Post by asimon on 2009-03-15
> **linuxisevolution said:**
> A half a year? That's all?
All I can say now. We will see how it looks then. The first distro (Fedora 11 AFAIK) with ext4 as default will get released shortly, thus we will see more and more heavy testing (and fixing) for ext4.

Also I have backups of my data, so a filesystem crash is not the end of the world for me. Of course my backup drive's filesystems will stay ext3 for longer.

> **linuxisevolution said:**
> I noticed your running Kubuntu, is it buggy still?
Of course. But it's getting better every day.

---

### Post by kayosiii on 2009-03-16
The Issue is this, ext3 will write a file to disk within 5 seconds of the application requesting it, ext4 this window extends to over a minute... This allows writes to be grouped together and thus be more efficient. Should the computer lock up or crash during that period the changes to the file will be lost. 

Because of the way that some programs work - they truncate the file to be 0 bytes in size and then write the file. There is a now a window where if the system crashes the file will end up being essentially blank. A future version of the kernel will include a patch for this that will narrow the window in specific instances. But it is the sort of thing that can only really be fixed upstream at the application level. So expect that chances of data loss in ext4 will be as great in the released version of jaunty.

---

### Post by asimon on 2009-03-16
> **kayosiii said:**
> The Issue is this, ext3 will write a file to disk within 5 seconds of the application requesting it, ext4 this window extends to over a minute...
Sorry for nitpicking but 'requesting it' can only mean fsync or fdatasync in which case ext3 and ext4 write their buffers to disc without delay. The problem is that applications are NOT requesting to write their to disc - close is not enough and never has been. Most depend on the behaviour of a single filesystem when we have around 60 others under Linux.

---

### Post by MadMan2k on 2009-03-16
> **linuxisevolution said:**
> 
Just a reminder, use the stable file systems, like:

ext2 ,ext3 , jfs, xfs, and reiserfs.
out of this list, EXT2, JFS and XFS will give you the same problems as EXT4.

besides the kernel in the current queue has patches for EXT4 which make it just as (un)safe as EXT3. 

[https://edge.launchpad.net/ubuntu/jaunty/+source/linux/2.6.28-10.32](https://edge.launchpad.net/ubuntu/jaunty/+source/linux/2.6.28-10.32)

---

### Post by zerted on 2009-03-16
Yes, I understand the buffering issues with ext4.  And when I'm on battery power, I prefer all writes to be stored in memory as long as possible.  What I don't understand is why all of Firefox's addon settings get wiped out.  Why would Firefox be touching all those unless I had the addon preferences open and was changing them?  Even Thunderbird only seems to have lost the basic profile info, not all my mail files themselves.  Reading a file shouldn't mean it has to be deleted.  

I'm a 'software engineer', but the only Unix/Linux development I've done has been through Java.  Thus I don't know what exactly all the different writing/flushing functions do.  Is there really a function that deletes a file as it is read?  Or are these programs reading the settings, wiping out their file contents, then rewriting the settings on exit?  In what case would that ever be a good design?

I've backed up all my files and plan to reinstall later today.  If someone wants me to test something about my freezing issues, I can only do that for a few more hours...

---

