---
title: "SSD Upgrade: I totally hosed it"
date: 2014-10-31
forum: Installation &amp; Upgrades
---

### Post by AFriendlyNerd on 2014-10-31
UPDATE: I figured it all out, thanks to lots of forum posts and GParted. If you find your NTFS partitions hosed by Clonezilla, read my third post below. Run chkdsk /f twice on the old partition, and then use GParted on a lived to merely copy and paste over the bad copy onto the new drive.

---
Original post:
It seems every time I do this, I fail to grasp certain things and break my server. Can you guys walk me back to being operational again?

I am running Ubuntu 14.04 on an ASUS X401a laptop, with the new UEFI style intel mobo. I had a 500GB drive with multiple formatted partitions, some the default linux format, a swap, a Windows partition, an NTFS and a FUSEBLK partition. I had it set up to boot into grub2, I think, and go to Ubuntu unless I make a different selection at the loader screen. My intent was to clone to a 1TB SSD.

I used Clonezilla but either it's not up to the task of multiple partition formats, or I needed to do more than follow the default tutorial.

----
NEW DRIVE:
The new drive boots up and there are key partitions missing (Ubuntu asks me if I want to press S or M), namely the NTFS partition that is critical to most of the operations of this media server. Maybe it's because all the numbers of the partitions are different, and I need to edit fstab? In the desktop GUI, Ubuntu only sees Ubuntu partition, I think.

---
OLD DRIVE:
So, I thought, no problem, I'll just boot from the old (now external) drive and try cloning it again. It boots straight into Windows 8.1 recovery mode, and I can't get it out. Clonezilla told me to run chkdsk on the windows partition, and I think I wound up overwriting the boot up method entirely. I booted up a LiveCD on USB, and tried the Boot Repair feature, but it seems to try and repair the New Drive. I can't figure out how to make it repair the old external drive.

I would rather not manually remove and insert these drives around again, because this is a cheap laptop that practically requires complete disassembly to change SSD's.

Please help me get either the new drive loading all partitions, or the old drive operational again so I can take another stab at cloning successfully.

---

### Post by AFriendlyNerd on 2014-10-31
Update: I booted a livecd, and used GParted to examine the new drive. Two partitions have exclamation marks and are "unknown". I believe the small one to be "linux-swap" on the old drive, and the big one is my critical NTFS partition. Its type is unknown and its flag is msftdata. I tried to use GParted to copy the NTFS partition from the old drive to the new, but GParted reported a one-cluster error in bitmap. It's telling me to run chkdsk /f twice on that partition, but it's not clear if it means the old drive's partition or the new one. Also, I think Windows is broken,  and if I make the wrong move I will also hose the grub2 bootloader on the new drive.

---

### Post by AFriendlyNerd on 2014-10-31
UPDATE 2:
I decided to forge ahead with chkdsk. Selected Windows from grub2. at the windows 8.1 repair options i navigated to command prompt. I used the command "wmic logicaldisk get name" and I got all the drive letters. I went to each drive letter, and if it was a windows or ntfs partition, I ran chkdsk /f twice.

Next, I booted up GParted from the Live CD again. I unmounted the NTFS partition on the old drive and am copying it to the new drive, overwriting the "unknown type" partition. Gonna take a while. Hope I'm not screwing up!

It worked!

---

### Post by oldfred on 2014-10-31
Did you copy the entire gpt partition structure to the SSD?

Windows has very specific partition requirements for UEFI boot. And order on drive is also important.
       Microsoft suggested partitions including reserved partition for gpt & UEFI:
[http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx](http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx)
Older Windows info on gpt - 2008 updated 2011
[http://msdn.microsoft.com/en-us/windows/hardware/gg463525.aspx](http://msdn.microsoft.com/en-us/windows/hardware/gg463525.aspx)
Windows technical info on gpt and GUIDs
[http://msdn.microsoft.com/library/windows/desktop/aa365449](http://msdn.microsoft.com/library/windows/desktop/aa365449)
Order on drive is important: msftres
[http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition](http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition)
Windows 8 info
[http://technet.microsoft.com/en-us/library/hh824947.aspx](http://technet.microsoft.com/en-us/library/hh824947.aspx)

And gpt has internal GUID in addition to the UUIDs, that cannot be on two drives. You cannot just image one partition.

 Do not use dd to copy partition with gpt due to unique guids & UUIDs post #12
[http://ubuntuforums.org/showthread.php?t=1680929](http://ubuntuforums.org/showthread.php?t=1680929)
Do not use dd with gpt partitions. Whole drive ok if old drive not used anymore, or no duplicates.
But do not use dd for copies from MBR to gpt partitioned drives, can use cp -a
[https://wiki.archlinux.org/index.php/Disk_Cloning](https://wiki.archlinux.org/index.php/Disk_Cloning)
Restore full drive dd backup - resync gpt partition tables and fsck pursuvant
[http://ubuntuforums.org/showthread.php?t=2145563](http://ubuntuforums.org/showthread.php?t=2145563)

---

### Post by AFriendlyNerd on 2014-10-31
Fred, 

Thanks for your time!

I have mostly solved this stuff, (I think/hope), and I have a couple of issues remaining. I do need to sort out the UEFI mess, I think, and I may still need to repair the Windows 8.1 OS. I will read your links regarding boot install and repair. I have a couple of external share mounts that are giving errors, so that's on my list.

Quick question: I still have the 8gig "linux-swap" volume. Is it still a good idea to have one, and if so, can I just use GParted to create that "unknown" partition into "linux-swap"?

UPDATE: Looks like the consensus is still that "swap" is a good idea.

---

### Post by AFriendlyNerd on 2014-10-31
Grub2/UEFI/bootloading actually works on this drive. I am good there. I am now adjusting the unallocated space to add to various partitions. I am still unclear if I can just create a new linux-swap and if I should, and what to do to fix my trouble with network shares giving mounting errors as Ubuntu boots up.

---

### Post by oldfred on 2014-10-31
I know nothing about mounting network shares, that would also be better in a separate thread.
Post fstab and mount. Not sure if it varies with type Samba, NFS, SSL etc? And then what underlying configuration is required. I do use NFS to copy from laptop to desktop and back, but scripted the setups and temporary mounts & rsync back & forth.

If a standard swap not an encrypted one, you can delete & create new with gparted. You just then have to update fstab with new UUID. It still should boot but will give errors on not mounting the bad UUID. Not sure how encrypted swaps work.

I still suggest some swap 2 or 3GB. Only if hibernating which usually is not recommended would you need swap equal to RAM in GiB not GB. I have 4GB of RAM and never use swap. But my old laptop with only 1.5GB uses swap as soon as I load more than one larger app and several small apps. But that is now how I usually work so Desktop with more RAM never gets full of active programs. RAM still fills up as a cache.

---

### Post by AFriendlyNerd on 2014-11-01
Thanks for your time, Old Fred! I guess I don't totally suck at Ubuntu anymore, being that I could dig myself out of a hole with a little handholding. I'll be much more prepared before my next such upgrade.

---

