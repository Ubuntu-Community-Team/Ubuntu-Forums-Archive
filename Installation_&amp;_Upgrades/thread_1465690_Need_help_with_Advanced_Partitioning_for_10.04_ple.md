---
title: "Need help with Advanced Partitioning for 10.04 please! (Yes, I'm a noob!)"
date: 2010-04-29
forum: Installation &amp; Upgrades
---

### Post by LinuxNeubie on 2010-04-29
I'm sure this is "old hat" for most of you non-rookies, but I'm in need of help on partitioning. Situation is this: I tried on numerous occasions to install various varieties of the OS (9.04, 9.10, 9.1 ALternate) all to no avail because we - being me and forum helpers - couldn't get any of them to work with my video card except on LiveCD in safe graphics mode.
So, I've booted the LiveCD and it works OK - not perfect mind you because it's still got a few lines here and there which I imagine can be fixed - but to the point, I will be deleting the old partition where 9.10 used to be installed and I need to know how to set it up properly. 

First it should be said that I triple-boot Ubuntu, XP and Windows 7. It handles all that fine. 

1. I need to know if the partition should be A) Primary or B) Logical
2. Location A) Beginning B) End
3. Use as: Ext4 journaling file system, Ext3, Ext2, ReiserFS, JFS, or XFS. It asks about fat16 or 32 but I'm almost sure I wouldn't want that.
Last, Mount Point. /, /boot, /home, /tmp, /vsr, /srv, /opt or /usr/local

I think some are obvious "not"s but since I'm virtually clueless I'm asking the experts! I appreciate your help!
THANKS!

---

### Post by srs5694 on 2010-04-29
For questions 1, 2, and 3, the answer is "any of the above (with one exception)." Linux is happy on either primary or logical partitions, at the start or end of the disk, and on any of the specified filesystems except for FAT. (Personally, I prefer ReiserFS for my main system and XFS for anything that'll hold big files; however, most Ubuntu users seem to use ext3fs or, more recently, ext4fs for everything.) Given that any given MBR disk can have only four primary partitions, it's probably best to use nothing but logical partitions for Linux, assuming the current partition layout enables you to do so.

As to mount points: Linux requires a root (/) partition. You can create additional partitions that are then accessed as directories off of that root filesystem, but this is an "and" proposition, not an "or" proposition. For instance, you can create a 20GB root (/) partition and a 100GB /home partition, but it's useless to create only a /home partition. (You could create only a root partition, though; everything else is optional.) Since user files go in /home, creating a separate /home partition effectively isolates your user files from the system, enabling safer and easier system upgrades in the future -- you can wipe out root (/) without touching your user files. You can also mount specific partitions read-only, use a mixture of filesystems optimized to specific purposes (as alluded to above), and just keep data on separate partitions to minimize the risk of a filesystem problem completely trashing everything on your system. Most installations also have a separate swap partition. This partition isn't mounted, but it is used to supplement RAM. The usual recommendation is to make it 1-2 times the size of your installed RAM. That will enable you to use a suspend-to-disk feature if you so desire, since the system saves all memory contents to the swap space when you use this feature.

IMHO, new users are best served by creating a 5-20GB root (/) partition and devoting the rest of the Linux system to /home. More advanced users or those with specialized needs (running a mail server or a MythTV system, say) may want or need to split off other partitions instead of or addition to /home. In a basic situation, how big root (/) should be depends on how much software you intend to install -- 5GB is enough for a minimal install, but 20GB may be required if you want to load the system up with lots and lots of software (GNOME, KDE, Xfce, every available Web browser, several office packages, software development tools, etc.).

---

### Post by LinuxNeubie on 2010-04-29
Well currently I only have 30gb allotted to it, although I have 800gb total, and available probably 100 I COULD use, but until I'm better with it than I am - which isn't very - based on what you say, since I have 2gb of RAM, a /swp of 4gb, / of 20 and /home of 5 should do initially. Since I don't yet know what file systems are better at what, and I'm sure there are reasons for each or there'd just be one, I'll just use ext4fs. I won't be using GRUB 2 since I've read that it could give problems with multiple boot OS's, or so it said was the case in 9.1. The issue may have been resolved in 10.04. Anyway, Once I know more what the fub I'm doing I can always rearrange things. 

One thing I didn't see was which "Mount Point" I should use. I would guess Boot, but guessing isn't usually a good thing when you're talking about the MBR on your main computer!

Thanks for the help and if you have any more suggestions I'd appreciate them! THANKS AGAIN!

---

### Post by LinuxNeubie on 2010-04-29
Well in re-reading, perhaps root / IS boot, so it becomes a moot point. Clarification always helps though!

---

### Post by srs5694 on 2010-04-30
Please re-read my second paragraph in my previous post. Instead of Windows-style drive letters, Linux uses a single unified filesystem. *All* files are accessed relative to the root (/) directory, and partitions are "mounted" at "mount points" (empty directories), so a partition's contents might appear under /home or /usr/local -- or these directories could be ordinary directories in the root (/) partition or in some other (for instance, if /usr is a separate partition, /usr/local might be an ordinary directory in /usr). The root (/) partition is required. All others are optional.

---

### Post by oldfred on 2010-04-30
Actually grub2 is better at finding other operating systems that are in working order. Sometimes users install grub into the windows partition in error and then windows is not functional, so grub will not find it. With old grub we often had to add manual entries for windows.

If you are planning on giving /home only 5GB I would not even make it a separate partition. I had just root & swap for 3 years with shared data in separate windows partitions. Only after 3 years and a new drive did I separate /home, which once you have used Ubuntu for a while is not real difficult to create after the fact. Only if you plan on upgrading RAM would I make swap 4GB. If RAM is 2GB make swap 2GB.

---

