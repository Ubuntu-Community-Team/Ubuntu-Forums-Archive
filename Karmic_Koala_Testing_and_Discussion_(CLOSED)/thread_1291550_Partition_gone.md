---
title: "Partition gone"
date: 2009-10-14
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by TheNessus on 2009-10-14
weird but maybe karmic-related.

I updated the system, and after reboot I could not see one of my NTFS partitions (for files, not OS). anyone has any ideas?

---

### Post by tuxxy on 2009-10-14
Load up gparted to get an overview of your partitions & hard drive. It's the Gnome Partition Editor tool in the menu.

---

### Post by TheNessus on 2009-10-14
well, Palimpsest Disk Utility recognizes it as "100gb unrecognised".  It does know its NTFS, but that's it.

---

### Post by tuxxy on 2009-10-14
You could try and mount it using Ubuntu.  Open a terminal and enter this command

```
mount -t ntfs-3g /dev/sda1 /mnt/mount -o force
```This example will force it to mount sda1, you will need to replace sda1 with your specific ntfs partition.  This should show you if the partition is corrupt.

---

### Post by kansasnoob on 2009-10-14
Maybe try installing ntfsprogs:

```
sudo apt-get install ntfsprogs
```

You may have to restart afterwards.

---

### Post by TheNessus on 2009-10-14
> NTFS signature is missing.
Failed to mount '/dev/sda5': Invalid argument
The device '/dev/sda5' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?That does not look promising... :(

kansasnoob, shall do. I should also state that it does not mount on Vista either.

---

### Post by tuxxy on 2009-10-14
> **TheNessus said:**
> That does not look promising... :(

kansasnoob, shall do.

ugh no it doesn't did you try and mount it in Windows.  Did you cold reset or something before this happened.

---

### Post by TheNessus on 2009-10-14
> **tuxxy said:**
> ugh no it doesn't did you try and mount it in Windows.  Did you cold reset or something before this happened.
yes, same result in Vista. 

Come to think of it, I did accidently clicked sleep when in Vista, when I intended to shut down, since the sleep fucntion hangs forever on my damned vista. It hanged, and I cold-reset it. It could very well be the reason...:(

---

### Post by TheNessus on 2009-10-14
well, thank you. you may close the thread or move it to the general help as solved. I guess...

I'll boot vista and use some excellent recovery tool I have there for a hellish scenario as this. you've been helpful. And Karmic is so damn good that I am sorry I blamed it!

---

### Post by tuxxy on 2009-10-14
> **TheNessus said:**
> well, thank you. you may close the thread or move it to the general help as solved. I guess...

I'll boot vista and use some excellent recovery tool I have there for a hellish scenario as this. you've been helpful. And Karmic is so damn good that I am sorry I blamed it!

Yes that is likely to be the cause then, when you sleep it puts all your saved files all over the drive and a cold shutdown could cause the hard drive to become corrupt.

---

### Post by ranch hand on 2009-10-14
I really hate to help people with Win Jerry Lewis Pro.  That said, there are an awful lot of really great data recovery tools out there.

I would quit trying to do anything with that partition and stay off Win and let the box run.

Do a search of recovery tools.  The good ones are LiveCDs with a linux base and lots of recovery tools on board.

Maybe others could give you recommendations but I am just a noob at this and only done any thing like that once.

All I will say is that it is amazing what you can recover.

It may be that the tools that you need are in the reops and you could install them and use them without rebooting.  Every time you reboot makes recovery a little harder.  Every time you try to look at the partition make recovery a little harder.  Get a good tool and turn it loose on it.

---

### Post by TheNessus on 2009-10-14
Welp, I only use it as a backup, and was afraid of using Vbox for a while. Used it now for some scanning. but well... can't do business with the devil it seems :D

---

### Post by ranch hand on 2009-10-14
I really would not give up on it at all.

All I was trying to get across is that the choice of people that really know what they are doing have been using Linux based tools for Win Whatever recovery.

I think part of it is that the way permissions are set in Win and Linux are different and the Linux stuff is just more powerful.  It may not be as pretty, or even have a gui, but it does the job.

Think of it as an adventure.  People pay money for that sort of thing.

Get your data back.  HAVE FUN.

---

### Post by TheNessus on 2009-10-14
well, since I do not know what I am doing, and I only use a terminal when I am absolutely sure of what I'm doing is ok (nothing/not much can go wrong), I'd prefer an win tool if it is available. Now, had I have the techy linux friend who got me into linux in the first place here with me, I'd give him the green light to use whatever linux tool there is to solve it. But I'm on my non-techy own here :D

---

### Post by kansasnoob on 2009-10-14
You can use ntfsfix after installing ntfsprogs as described here:

[http://mpathirage.com/how-to-fix-ntfs-mount-error-on-ubuntu/](http://mpathirage.com/how-to-fix-ntfs-mount-error-on-ubuntu/)

It's easiest if you still have Windows installed in a dual boot because you can just boot up Win after running chkdsk and Win will run a check and usually get things sorted.

---

### Post by ranch hand on 2009-10-14
There is something to say for familiarity.

I just think that your odds would be better from your Ubuntu installation.

MS ought to be able to have a usable recovery tool though.  Their OS' are good at making you need one.

Hope you get it all back.

When (not if) you do, I would shrink the bugger to the smallest you can stand.  Then I would put in an ext4 partition.  You could back up to the win partition and then transfer it to the ext4 partition from Ubuntu.

This would make it much more secure.  Win does not support ext4, can't recognize it.  When you need something for Win you could just dump it back in.

---

### Post by Zorael on 2009-10-14
testdisk can scan for lost partitions, can't it? I've had it recreate my whole partition table after a particularly nasty (Windows) malware hit me.

---

### Post by VMC on 2009-10-14
> **Zorael said:**
> testdisk can scan for lost partitions, can't it? I've had it recreate my whole partition table after a particularly nasty (Windows) malware hit me.

I've heard of some great results from using testdisk, but the OP seems to have a strange problem. At least it appears so.

```
Following are some of the main features of TestDisk:

*Fix partition table, recover deleted partition
*Recover FAT32 boot sector from its backup
*Rebuild FAT12/FAT16/FAT32 boot sector
*Fix FAT tables
*Rebuild NTFS boot sector
*Recover NTFS boot sector from its backup
*Fix MFT using MFT mirror
*Locate ext2/ext3 Backup SuperBlock

The following types of file systems/partitions are supported:

BeFS ( BeOS )
DOS/Windows FAT12, FAT16 and FAT32
HFS and HFS+, Hierarchical File System
Linux Ext2 and Ext3
Linux Raid (Raid 1,4,5 and 6)
Novell Storage Services NSS
NTFS ( Windows NT/2K/XP/2003/Vista )
Sun Solaris i386 disklabel
Unix File System UFS and UFS2 (Sun/BSD/…)
```

---

### Post by psyke83 on 2009-10-14
> **VMC said:**
> I've heard of some great results from using testdisk, but the OP seems to have a strange problem. At least it appears so.

No, testdisk is exactly what the OP should try using. My partition layout was accidentally overwritten and testdisk managed to reconstruct the NTFS partition. It's definitely worth a try.

---

### Post by ranch hand on 2009-10-14
Well I guess these guys with Win Jerry Lewis Pro are a big help.

I not only am a ranch hand, a bunch noted for being willing to jump into things, I am also a Blacksmith, a bunch who like to see how things work, if a big hammer is involved - all the better.

I have a couple of HDDs that have suffered from the "well what happens if I do this" meathod of learning to partition drives.  Basically I succeeded in wiping ALL info off these drives.  This makes them real hard to detect.

There is at least one that bios will see even if nothing else will.

I downloaded this here testdisk thingy.  I think I may have to turn off my internal drives and hook those bricks up and see if they are detected by this.  It will write info to the MBR which will in turn make the disk visible and therefore usable.

If it works or not it will be FUN, so I must thank the OP for starting this thread and VMC for a new toy.

---

### Post by kansasnoob on 2009-10-15
> **psyke83 said:**
> No, testdisk is exactly what the OP should try using. My partition layout was accidentally overwritten and testdisk managed to reconstruct the NTFS partition. It's definitely worth a try.

I think though, from reading all of the op's posts, that the partition is "in tact" and simply can't be mounted because it wasn't "unmounted" properly.

Always hard to tell unless the box is right in front of you. But, hell yeah, testdisc and/or photorec are great!

---

### Post by TheNessus on 2009-10-19
testdisk worked; thanks guys. I couldn't get it to mount but the program itself managed to load my stuff which I copied and backed up.

---

### Post by ranch hand on 2009-10-19
That is the important thing.  Save the data first.  Try to recover the bugger second.  You may get it yet and now you can try off the wall experimental techniques (fancy way of saying "well what happens if I push this button while my finger is in the socket" kind of thing).

---

