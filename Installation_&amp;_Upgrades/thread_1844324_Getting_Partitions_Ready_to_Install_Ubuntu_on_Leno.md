---
title: "Getting Partitions Ready to Install Ubuntu on Lenovo ideapad Z570"
date: 2011-09-14
forum: Installation &amp; Upgrades
---

### Post by peGGi on 2011-09-14
Hi, 

I've been doing some research around partitioning and installing Ubuntu on my Lenovo ideapad Z570 as part of a dual-boot set-up with Windows.  My system comes pre-installed with a pretty complicated partition system.  I've included a screen-grab with this post and I describe these partitions below.  I've pretty much read all of these forums and webpages which pertain to partitioning, etc. 

[LIST]
[*][http://forums.lenovo.com/t5/IdeaPad-Y-U-B-V-and-Z-series/new-disk-partioning-and-one-key-recover-feature/td-p/368325](http://forums.lenovo.com/t5/IdeaPad-Y-U-B-V-and-Z-series/new-disk-partioning-and-one-key-recover-feature/td-p/368325)
[*][http://forums.lenovo.com/t5/Linux-Discussion/Factory-Windows-7-partitions/td-p/535363](http://forums.lenovo.com/t5/Linux-Discussion/Factory-Windows-7-partitions/td-p/535363)
[*][https://help.ubuntu.com/community/forum/installation/Partitioning](https://help.ubuntu.com/community/forum/installation/Partitioning) 
[*][http://en.wikipedia.org/wiki/Disk_partitioning](http://en.wikipedia.org/wiki/Disk_partitioning) 
[*][https://help.ubuntu.com/10.04/installation-guide/amd64/non-debian-partitioning.html](https://help.ubuntu.com/10.04/installation-guide/amd64/non-debian-partitioning.html)
[/LIST]
 
Ideally, what I would like is to have a partition of 80Gb for Windows, a partition of 80Gb for Ubuntu, a large partition for data that Ubuntu and Windows can share, plus whatever other partitions Lenovo's programs and back-up applications need. 

Having read through the above forums plus other information regarding partitions, I've come to understand the following things:
 
[LIST=1]
[*]That a hard-disk drive can only have maximum 4 primary partitions or 3 primary partitions and an extended partition.
[*]That the extended partition may in turn be subdivided into several logical partitions.
[*]That Windows must be installed on a primary partition with the boot files.
[*]That Ubuntu can be installed on a primary or a logical partition.
[/LIST]

Are all of the above correct?   

If so, my questions are:
[LIST=1]
[*]I currently have three primary partitions and one logical (a tiny hidden system one *primary*, I assume for recovery; the large C: with Windows *primary*; the *logical* partition, D: Lenovo with Lenovo progam files and drivers; and a hidden "LENOVO_PART" *primary* partition which I assume is where Lenovo's back-up app creates some sort of system image...)  Does that mean that I already have 3 primary partitions and one extended partition, which is also one logical partition, or is the second partition an extended partition subdivided into the primary C: and the logical D: ?
[*]When I install Ubuntu, will the installer's partition tool be able to create a partition for Ubuntu with its Ext3 file-system and a partition for data in NTFS that Ubuntu and Windows can share?
[/LIST]

My main concern is how I can safely resize to accommodate a drive for Ubuntu and a large data drive.   

I'm thinking of two paths:
[LIST=1]
[*]First is to downsize the C: drive to 80Gb, then create an extended partition with the space and divide that into two logical partitions, one for Ubuntu and one for data.  But the fact that the D: Lenovo partition is already logical confuses me...
[*]The other is to merge the C: drive with the D: drive, then create an extended partition with two logical partitions (Ubuntu and data).  I'm afraid this way I might ruin the Lenovo programs and drivers...
[/LIST]

Sorry for this lengthy post but I want to show that I've tried researching it but I'm stuck....  Any advice at all?  Any advice would be very much appreciated.  I'm excited and impatient to get Ubuntu up and running but there's so much to figure out first! :)

---

### Post by oldfred on 2011-09-15
If you have an extended it may make it easier, but you still will have to do some shuffling of partitions and sizes. You can only have one extended so if you shrink c: and the  unallocated is next to the extended then you can move the extended to include the unallocated. In the extended you can then create partitions for / (root) & swap. If you are storing most of your data in a shared NTFS partition you may not even need a separate /home as then it will only contain the hidden user settings & folders. (Still backup /home regularly.)

Make a set of recovery DVDs from the Lenovo backup. And make a Windows repairCD from Windows before doing anything. You may also want to do a full back up of windows as the recovery DVDs will only restore to as purchased and you then have to run all the updates, houseclean the cruft, and restore your data.

Make your own Windows recoveryCD/repair:
[http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc](http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc)
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

Some portables may have special keys to do some functions. You may loose those. I might separately backup the MBR as even restoring a standard Windows boot loader may not include those functions.

Be very careful using dd, its other name is data destroyer as a typo can cause major damage. i.e. - reversing the if and of commands then writes the data the wrong way.
Backup MBR
[https://help.ubuntu.com/community/WindowsDualBoot#Master%20Boot%20Record%20backup%20and%20re-replacement]("https://help.ubuntu.com/community/WindowsDualBoot#Master%20Boot%20Record%20backup%20and%20re-replacement")
Backup the MBR e.g. 
sudo dd if=/dev/sda of=mbr.bin bs=446 count=1

post this from the Ubuntu liveCD, or a screenshot from gparted. This will show partition layout. Do not create any partitions from Windows, but use Windows to defrag & then shrink the Windows C: partition. Reboot into Windows several times as it will want to run chkdsk.

sudo fdisk -lu

Test that liveCD works well with your system before making any system changes.

---

### Post by peGGi on 2011-09-15
Hi oldfred, I really appreciate your help, especially so quickly.  

> **oldfred said:**
> If you have an extended it may make it easier, but you still will have to do some shuffling of partitions and sizes. You can only have one extended so if you shrink c: and the  unallocated is next to the extended then you can move the extended to include the unallocated. In the extended you can then create partitions for / (root) & swap. If you are storing most of your data in a shared NTFS partition you may not even need a separate /home as then it will only contain the hidden user settings & folders. (Still backup /home regularly.)

So what you're saying here is shrink C: in Windows, so then I'll have unallocated space between the primary C: and the logical D: .  Then in GParted, I can sort of make the logical D: take over the un-allocated space, then split that entire logical partition into 3 logical partitions - the original D:, the ubuntu system one, and the data partition?  Have I got that right?  I'm worried here about preserving the data on D: .  I don't quite understand what "/ (root) & swap" means I'm afraid.

> **oldfred said:**
> Make a set of recovery DVDs from the Lenovo backup. And make a Windows repairCD from Windows before doing anything. You may also want to do a full back up of windows as the recovery DVDs will only restore to as purchased and you then have to run all the updates, houseclean the cruft, and restore your data.

Make your own Windows recoveryCD/repair:
[http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc](http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc)
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

I have already made a Windows repair CD and the OEM factory recover DVDs.  I've also backed-up all of Windows as it is now to my external HDD twice, using both the OEM app and EaseUs backup.  So hopefully I'm well backed-up.

> **oldfred said:**
> Some portables may have special keys to do some functions. You may loose those. I might separately backup the MBR as even restoring a standard Windows boot loader may not include those functions.

Be very careful using dd, its other name is data destroyer as a typo can cause major damage. i.e. - reversing the if and of commands then writes the data the wrong way.
Backup MBR
[https://help.ubuntu.com/community/WindowsDualBoot#Master%20Boot%20Record%20backup%20and%20re-replacement]("https://help.ubuntu.com/community/WindowsDualBoot#Master%20Boot%20Record%20backup%20and%20re-replacement")
Backup the MBR e.g. 
sudo dd if=/dev/sda of=mbr.bin bs=446 count=1

I read that page but this is the thing that's most confusing me.  I agree that it would be smart to back-up the MBR as my OEM's back-up utility might be lost if I'm resizing partitions.  Are you saying that I should boot up Ubuntu from the liveCD, open terminal, enter "sudo dd if=/dev/sda of=mbr.bin bs=446 count=1" and this will have backed up the MBR?  Where will that file be saved?  

I'm sorry if this seems obvious to you.  I'm very new to all this and it's a bit of a struggle, but I'm trying!  

I have tried out Ubuntu from the liveCD and it seemed ok apart from getting wireless working.  I've since read up on it and got drivers from Broadcomm so I hope it'll be ok in final installation.  But for now I just wanna make sure that I get the partition right without ruining my system!  

Thank you for your help.

---

### Post by peGGi on 2011-09-15
Hi,

I think I get "/ (root) & swap" now.  The \ (root) is where ubuntu's system files and software etc. will be installed.  Swap is a small partition for virtual memory.  

My intention was to use the data share NTFS partition as the equivalent of \home.  My ultimate goal is to get Ubuntu up and running and use it for most everything...  I only want to keep Windows as a back-up.  I won't be moving using files back and forth between the two often.  

So if I understand all this correctly, I'm going to reduce C: and create empty space.  Then when I install Ubuntu, I will use that empty space to create \ (root), the NTFS shared data partition, and swap.  So eventually my hard-drive will be divided as follows:

1. Small hidden, OEM boot partition *primary*
2. C: with Windows *primary*
3. D: with Lenovo program files *logical*
4. / (root) with Ubuntu *logical*
5. data partition (used as home but also accessible by Windows) NTFS *logical*
6. Swap partition *logical*
7. Hidden "LENOVO_PART" partition *primary*

Have I got it right?  Will I be moving the D: partition to the beginning of that empty space, and creating the Ubuntu partitions after it?  

I'm also wondering if there is any point in keeping that "LENOVO_PART" partition if my Lenovo's back-up software isn't going to recognise the partitions afterwards anyway...  It's a waste of 30Gb or so of space...

---

### Post by oldfred on 2011-09-15
Partitions look ok, but a few comments. You will have to expand the extended partition into the unallocated first as it is the container for the logical partitions.

You can store data in the NTFS partition and even link in folders to /home but you cannot make a Windows partition /home. All Linux system partitions including /home must be Linux formats to support ownership & permissions.

Not sure if your current d: is where you want your data or not. You can also create another NTFS which in Windows will be e:.

Not familiar with Lenovo's layout. Many with HP have deleted the Vendor recovery after creating one or even two copies. Many also delete the vendor utilities partition. With HP they are not used much, easily backed up and also available from HP. Does Lenovo let you download some or all of its files? 

What version of Windows. If Vista or 7 be sure to use the Windows tools to shrink partitions but do not create any with Windows. Use gparted to create partitions and use manual install (Something Else in Natty) to choose which partition to use.

Basics of partitions:
[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)

Shared NTFS partition - You can also use links
[http://www.howtogeek.com/howto/35807/how-to-harmonize-your-dual-boot-setup-for-windows-and-ubuntu/](http://www.howtogeek.com/howto/35807/how-to-harmonize-your-dual-boot-setup-for-windows-and-ubuntu/)

Ownership and permissions of vfat / ntfs are set at the time of mounting. This is often a source of confusion.
[http://www.psychocats.net/ubuntu/mountwindowsfstab](http://www.psychocats.net/ubuntu/mountwindowsfstab)
HOWTO: Mount NTFS partitions with specific ownership/permissions - WorMzy
[http://ubuntuforums.org/showthread.php?t=1604251](http://ubuntuforums.org/showthread.php?t=1604251)

---

### Post by peGGi on 2011-12-01
An extremely belated but heartfelt and appreciated thanks, oldfred, for your help!  

I kind of gave up on trying to sort all this out in September but I'm having another stab at it.  

After extensive reading (from your links and elsewhere), I've decided to do the following:

1. Shrink the C: drive with Windows
2. in G-parted, when I install Ubuntu, extend the D: (logical) to encompass all of the newly created preceding free space.
3. Shrink this D: drive to about 30 Gb (I think it's easier just to keep this vendor partition with it's drivers, software, etc.)
4. Create 3 new logical partitions with the free space - one for /home (which I hope to be able to access from Windows using Ext2Read), another for swap, and one for / root).

If the vendor back up software isn't usable after all this, then I'll delete that final, hidden partition and expand the /root partition to use the space.  This is why I hope to put swap before / root.  Does it matter if swap is before or after?  Any final comments/suggestions/prayers ;) ?

---

### Post by oldfred on 2011-12-01
If you have a fair amount of RAM, swap does not get used much unless you edit video files or load every program at once. Some used to think it made a bit of difference to have it on the part of the drive that is a bit faster, but it really does not make any difference where swap is.

More info on swap
[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

I think the Linux NTFS driver is more reliable than any of the Windows drivers that try to read Linux files. Too much permissions, ownership & other issues to manage. Best just to have a e: drive as NTFS and have all your data in that. You can link or mount the NTFS folders into your /home so it looks like your data is in /home even though it is in another partition. I have my Firefox & Thunderbird profiles in a shared NTFS partiiton and use profile.ini to redirect to the shared folders in both XP & multiple installs of Ubuntu.

---

### Post by peGGi on 2011-12-01
I really appreciate this, it's so helpful.  This is exactly the information I need.  And I find that I've been reading so much about this stuff that it's hard to keep it clear in my head.

I will do as you advise and keep the shared data partition as NTFS, and not the /home partition.

Do you still think it would be wise to have separate, small partitions for the actual /home and for /root - I read that if I want to reinstall or upgrade Ubuntu later, that it's good to keep them separate, as all my settings, etc., will still be there.

---

### Post by oldfred on 2011-12-01
For new users I often suggest a separate /home as it has both user settings and all your files. But if you put all (or most) of your files in a shared NTFS partition your /home is small and easily backed up. 

For more advanced users I suggest a separate /mnt/data (ext4) partition so then you do keep /home inside / (root). My /home is under 2GB with all data in both a shared NTFS partition and a ext3 data partition. The shared is left over from when I dual booted XP which I rarely boot anymore. But I have not reconfigured all the data in the shared NTFS, yet. Most of my /home is .wine (about 1.2GB) and that is the Windows version of Picasa. The actual users settings are small and easily to backup.

The advantage of a separate /home is reinstall in place. All your user settings are not overwritten as long as you remount the existing /home and DO NOT format it on a new install. If you have hard drive space for another 20GB it is even easier to create another system (/) and have two installs - on older and the current. Then you can copy over any old settings if need be.

Whichever you do you still need to backup /home on a regular basis.

All of above may be too much for a new user, ignore and just install it and have fun with Ubuntu. I only had / (root) & swap with a shared NTFS for about 2 years, before I started changing to more partitions.

---

### Post by peGGi on 2011-12-01
ok great, thanks.  

i'll mull it over and let you know what i do, in case you're curious!

thanks again for all the help.  has been tricky getting my head around partitions.

---

