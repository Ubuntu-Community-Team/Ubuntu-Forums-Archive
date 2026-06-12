---
title: "partition issues on existing Windows 7 machine"
date: 2010-05-20
forum: Installation &amp; Upgrades
---

### Post by rlinger on 2010-05-20
I'm having a installation problem. I am trying to install Ubuntu on my laptop that is currently running Windows 7, and win7 is needed for use in projecting songs in our church services. The HD is a 500 gb already partitioned with the max. of 4 partitions. Win7 files are on the sda2 partition and my data files are on sda3. Sda1 and sda4 are smaller partitions, one is 3 gb's the other is 1 gb.

My question is, what is the best set up for me to install Ubuntu? I can't create an extended partition since I already have 4 partitions. I like my current partition set up as far as windows goes, but I would really like to get Ubuntu installed.

I'm fairly new with Ubuntu, I like what I've seen so far. I had it installed with wubi in windows XP on a laptop that I just sold, and I've upgraded to the windows 7 laptop now, and I'm stuck!

_***HELP!!!***_

Thanks,
Rob

---

### Post by darkod on 2010-05-20
It all depends what you have on sda1 and sda4. If you created those partitions and just have some smaller files there, move them temporarily to external hdd or to sda3, delete the small partition, and that would allow you to create extended partition which can have: the small 1GB ntfs partition again, ubuntu root, ubuntu swap (and ubuntu separate /home if you plan on having one).

Win7 will have no problem reading the small 1GB ntfs as logical partition inside the extended. Usually just the win7 system partition has to be primary. Your data partitions can be logical.

But if sda1 and sda4 are some sort of system, or utility, or tools partitions, moving them on logical partition might not work.

Of course, even if moving works, you still have to shrink either sda2 or sda3 to make unallocated space for ubuntu. It's best to shrink from inside win7 using Disk Management, and then boot win7 few times so it can do its disk checks.

---

### Post by srs5694 on 2010-05-20
If I understand correctly, /dev/sda3 is a normal data partition with no special system functions. If so, it should be possible to convert it into a logical partition inside an extended partition and resize it or /dev/sda2 to make room for Linux in the extended partition. This operation is, however, a bit tricky, at least using the tools with which I'm familiar. If you need exact instructions, please boot a Linux emergency disc such as [System Rescue CD](http://www.sysresccd.org/) or [PartedMagic,](http://partedmagic.com/) start a text-mode command shell, type "fdisk -lu", and post the results here. (You can cut-and-paste the output into a text file that you store on a USB flash drive or even your Windows data partition.) Please post the output between "[noparse]```
[/noparse]" and "[noparse]
```[/noparse]" strings to improve legibility. Also, please say which partition (/dev/sda2 or /dev/sda3) you intend to shrink to make room for Linux (or both, if you want to take a bit of space from each of them).

You're well advised to make a complete backup of your hard disk before you attempt this. The sort of partition resizing and moving operations required can result in loss of all data on the partitions in the event of a power failure or other problem, so having a backup is important insurance.

---

### Post by rlinger on 2010-05-20
Thanks for your quick replies guys, that's what I like about this community!

First off, my plan was to decrease the size of sda2 by 30 gb. Secondly, sda4 is roughly 2.5 gb's in size, and has 1.39 gb's of used space. My problem is knowing what's in that drive. I'm not sure I want to just delete that drive.

Here's the break down of my drive (shown in GParted):

unallocated         1.0  mb
/dev/sda1         15.0  gb         labeled: pqservice      12.02 used
/dev/sda2      226.38 gb    labeled: acer                      85.81 used
/dev/sda3      220.90 gb    labeled: data                      15.97 used
unallocated          1.0  mb
/dev/sda4             3.48 gb    labeled: (empty)              1.39 used


Like I said I was planning on reducing the sda1 partition by 30 gb, and using that for my Ubuntu install, using it to create an extended partition, with at least 3 logical partitions.

Is there a way to find out just what's in the sda4 partition? Looking at the Disk Manager in win7, its called out as "Healthy (OEM Partition)"

---

### Post by srs5694 on 2010-05-20
Don't worry about /dev/sda4. It's small enough that it won't get you a lot of space if you delete it.

The procedure for converting /dev/sda3 into a logical partition is as follows:


[LIST=1]
[*]Boot Windows.
[*]Use the Windows disk utilities to shrink /dev/sda2 (presumably C: in Windows) by the desired amount. Be sure to shrink it *from the end,* not from the beginning -- you  want free space between /dev/sda2 and /dev/sda3.
[*]Boot an emergency disc, such as the ones I referenced in my previous post.
[*]Launch the GParted partition-editing software and verify that there's free space between /dev/sda2 and /dev/sda3. Exit from GParted.
[*]Launch a text-mode shell (usually called "Terminal," "Konsole," or "xterm").
[*]In the shell, type "sfdisk -d /dev/sda > parts.txt". This should create a file called parts.txt.
[*]Copy parts.txt to a USB flash drive or some other removable disk. This is insurance in case something goes wrong.
[*]Edit the original parts.txt file. Cut-and-past the entry for /dev/sda3 to the end of the file and change "/dev/sda3" to "/dev/sda5". Then edit the original /dev/sda3 entry. Decrease its "start=" value by 1, increase its "size=" value by 1, and change its "Id=" value from "7" to "f". Save these changes.
[*]Type "sfdisk /dev/sda < parts.txt". If you get an error message about the program not liking the partitions, review your changes to be sure they're sane and, if they are, type "sfdisk --force /dev/sda < parts.txt".
[*]Reboot into Windows and check that it still boots and that your data partition (probably [noparse]E:[/noparse] is still accessible. If it's not, reboot the recovery disk and restore the backup of parts.txt that you created earlier. Review your process; maybe you made a mistake in editing parts.txt.
[*]Reboot into your recovery disk.
[*]Launch GParted.
[*]Use GParted to resize /dev/sda3 (the extended partition, which is just a carrier for logical partitions) to fill the space left by resizing /dev/sda2.
[*]Optional: Move and/or resize /dev/sda5. Moving it adjacent to /dev/sda2 will slightly speed up accesses to it from Windows, but this operation will take time and can be a bit risky.
[*]Create new partition(s) in the free space for Linux.
[/LIST]


You should now be able to reboot and install Linux. Select the "advanced" or "manual" partitioning option (I don't recall which it's called) and select the partition(s) you created at the end of the preceding procedure for installation.

Note that this procedure is risky. The riskiest steps are the partition resize/move operations and the use of sfdisk to write the changed parts.txt file. Any of these steps, if done incorrectly, can render a system unbootable or trash a partition. I strongly recommend you make backups of your important data before you begin. Unfortunately, the only alternative to taking at least some of these risks is to install Linux on an external drive. That would enable you to leave your internal hard disk mostly or completely untouched, but of course you'll have to buy it and carry it around with you.

Good luck!

---

### Post by rlinger on 2010-05-20
Thanks!

I'll have to try this tomorrow, I have a busy schedule this evening. I want plenty of time to do these steps. I don't want to reinstall Win7, since it was a upgrade from Vista.

I did reduce the sda2 (windows C drive) by the 30 gb originally, using windows 7, and that went smoothly, but I placed that 30 gb back into it once I realized that I already had 4 partitions. So the resizing of the sda2 partition isn't the hard part for me.

Thanks again for your input! I'll let you know how it went.
Rob

---

### Post by bcbc on 2010-05-20
wouldn't be a whole lot simpler and safer to 
1. backup the used 16gb from the data partition in sda3 to the windows partition sda2
2. delete the sda3 partition and recreate it as an extended.
3. create a new logical data partition in the extended, as well as the new logical partitions for linux (using live cd - actually you could do most of this in windows)

Using sfdisk to manually mess with the partition table seems over the top (and yes 'risky' is an understatement).

---

### Post by darkod on 2010-05-20
> **bcbc said:**
> wouldn't be a whole lot simpler and safer to 
1. backup the used 16gb from the data partition in sda3 to the windows partition sda2
2. delete the sda3 partition and recreate it as an extended.
3. create a new logical data partition in the extended, as well as the new logical partitions for linux (using live cd - actually you could do most of this in windows)

Using sfdisk to manually mess with the partition table seems over the top (and yes 'risky' is an understatement).

+1

Much better. Only to add, step 0, shrink /dev/sda2 by the 30GB as you planned. That is if you want to keep the same size for /dev/sda3.

Then move the 15GB data temporarily, delete the partition, and use all the unallocated space for extanded partition, creating the ntfs data partition inside.

---

### Post by bcbc on 2010-05-20
> **srs5694 said:**
> 
6. In the shell, type "sfdisk -d /dev/sda > parts.txt". This should create a file called parts.txt.
7. Copy parts.txt to a USB flash drive or some other removable disk. This is insurance in case something goes wrong.


The sfdisk manual recommends using the -O option if creating logical partitions. > BE EXTREMELY CAREFUL - ONE TYPING MISTAKE AND ALL YOUR DATA IS LOST

As a precaution, one can save the sectors changed by sfdisk:

% sfdisk /dev/hdd -O hdd-partition-sectors.save
...
%
Then, if you discover that you did something stupid before anything else has been written to disk, it may be possible to recover the old situation with

% sfdisk /dev/hdd -I hdd-partition-sectors.save
%
([COLOR="Red"]This is not the same as saving the old partition table: a readable version of the old partition table can be saved using the -d option. However, if you create logical partitions, the sectors describing them are located somewhere on disk, possibly on sectors that were not part of the partition table before. [/COLOR]Thus, the information the -O option saves is not a binary version of the output of -d.)

---

### Post by -kg- on 2010-05-20
> **darkod said:**
> 
>  Originally Posted by bcbc  View Post
wouldn't be a whole lot simpler and safer to
1. backup the used 16gb from the data partition in sda3 to the windows partition sda2
2. delete the sda3 partition and recreate it as an extended.
3. create a new logical data partition in the extended, as well as the new logical partitions for linux (using live cd - actually you could do most of this in windows)

Using sfdisk to manually mess with the partition table seems over the top (and yes 'risky' is an understatement).

+1

Much better. Only to add, step 0, shrink /dev/sda2 by the 30GB as you planned. That is if you want to keep the same size for /dev/sda3.

Then move the 15GB data temporarily, delete the partition, and use all the unallocated space for extanded partition, creating the ntfs data partition inside.

+1 from me, as well.  To go through all those gyrations just to convert a Primary partition to a Logical one...playing with the partition table all the way...while that partition is a data partition with 15 GB of data on it seems ludicrous to me, especially when you have all that room on sda2.

My addition to this would be...how much space do you anticipate needing on sda3 for future data?  Since you only have 16 GB on a 221 GB partition, you could easily just recreate that partition as around 199 GB inside the Logical partition and have the same effect.

My suggestion would be to copy your data from sda3 over to sda2, delete sda3, create an Extended partition filling that 221 GB, recreate your sda3 inside the Extended partition (of course, that will be sda5 after recreation) around 30 GB or so smaller than the original.

You can then copy your data files back into sda5 and install in the free space inside the Extended partition.  Windows won't even realize what happened because, as it won't "see" the Linux partitions (and doesn't use the "sda(x)" convention in labeling its partitions), the partition will still be Drive D (I'm assuming that sda1 and sda4 are hidden partitions as far as Windows is concerned).

---

### Post by srs5694 on 2010-05-20
I'll retract my earlier procedure, at least for rlinger. I didn't notice the statement of how much space was in each partition when I wrote my previous post. The other posters are correct that it will be simpler and safer to back up /dev/sda3, delete it, and re-create it as a logical partition. I'm leaving the description in place in case somebody might run across this thread in the future and find it useful.

Yes, adding -O to the sfdisk call to write partitions will add to the safety. It would only help if the new extended partition overlapped a primary partition, though. I suppose that might be the case if you accidentally deleted a digit or two from the extended partition's start point.

---

### Post by -kg- on 2010-05-20
As an addendum, it will save quite a bit of time, too.  Resizing partitions of that size takes a lot of time (and may cause you to lose data and files), while deleting and recreating them takes almost no time at all, even adding in copying and copying back 15 GB of data.

That's why I suggested recreating sda3 around 30 GB smaller for your installation rather than resizing sda2.  Resizing sda2 would take *mondo* time and put your installation files at risk of loss.

---

### Post by rlinger on 2010-05-21
Thanks for your input guys! I think I'm going to do what kg suggested, move my data files onto sda2, delete and recreate sda3 and go from there. BTW, I am one of a very few that have bucked the Ipod trend and I went with the ZuneHD. As a result, I need a windows option to sync my music and videos to the Zune. As for the large sda3 data size, this is where all my music, videos, drawings (I'm a architectural draftsman, using CAD) and other stuff, so it does need to be pretty large, but stealing the 30 gb's from there shouldn't be a problem.

Here's another question, which partition should I delete and copy into the extended partition, the 15 gb sda1 or the 3.5+/- gb sda4? I understand that before doing anything to either I need to shrink one of my other partitions.

Thanks again for your help guys, this newbie appreciates it!
Rob

---

### Post by bcbc on 2010-05-21
> **rlinger said:**
> Here's another question, which partition should I delete and copy into the extended partition, the 15 gb sda1 or the 3.5+/- gb sda4? I understand that before doing anything to either I need to shrink one of my other partitions.
Rob

I'm not sure I understand why you want to get rid of sda1 or sda4. You don't need to. Just backup your data from sda3, delete it and recreate it as an extended partition. Unless you feel the need to take space from sda1, in which case shrink this first from windows, before recreating sda3.

If you have any questions ask first here and someone will guide you.

Note: when you install ubuntu 10.04 there is a part where it asked you where to install the grub bootloader and suggests 'all partitions if not sure'. DO NOT do this. Install it to **/dev/sda** only.

---

### Post by rlinger on 2010-05-21
Ok, everything went fine, I'm currently transferring the data files back to windows drive D. Ubuntu started and runs fine. It does look though like grub is running a little strange though. When the computer first boots up, I get the screen that shows 5 or 6 options; starting Ubuntu 10.04, ubuntu 10.04 recovery, Windows 7, etc., then after making my choice to start windows 7 it takes me to the windows 7 or ubuntu start up screen. On my old XP laptop, where I installed ubuntu with wubi, these two screens came in opposite. Can I do anything to get that back to how it was, or is it too late?

---

### Post by bcbc on 2010-05-21
If you had an old wubi you should be able to manually delete the entry from your windows menu. Go to [https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide) and look for the entry to manually uninstall it.

If you want to make your grub menu look more like the old menu, e.g. default to windows and only have two choices (windows or ubuntu), then this is a really good guide that I have used: [http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Custom_Menu](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Custom_Menu)

---

### Post by rlinger on 2010-05-24
> **bcbc said:**
> If you had an old wubi you should be able to manually delete the entry from your windows menu. Go to [https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide) and look for the entry to manually uninstall it.

The wubi was installed on my old laptop, and only mentioned because that was my first and only experience with Ubuntu, and I actually liked the boot up sequence on that machine.

As for the install, like I said, all went well, been using both OS's all weekend, even used and edited Audacity files between both OS's without any problems.

_**Thanks again for all your help guys!**_  :P

Rob

---

