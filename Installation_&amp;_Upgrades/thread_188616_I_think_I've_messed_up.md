---
title: "I think I've messed up"
date: 2006-06-04
forum: Installation &amp; Upgrades
---

### Post by percy1 on 2006-06-04
I tried to partition my Windows XP Fat32 harddrive for the purpose of creating a dual booting system with Dapper.

I managed to create a new partition, unfortunately I seem to have fubar'ed the rest of the harddrive. The XP partition is now describing itself as having an extended 2 file system, and everything "appears" to have been wiped off it. Also, the harddrive is now unmountable in Ubuntu and I can't seem to read it in Windows either.

Is there anything I can do to recover my harddrive?

---

### Post by rcarring on 2006-06-04
Boot with your XP cd and attempt to repair from the recovery console.

It's possible you have indeed wiped your XP drive, but how would XP be able to tell you it's file system is changed if everything appears to have been wiped off.

---

### Post by percy1 on 2006-06-04
> It's possible you have indeed wiped your XP drive, but how would XP be able to tell you it's file system is changed if everything appears to have been wiped off.
Sorry if I wasn't clear. I connected my "wiped out" harddrive to another PC to check out what had happened. When I tried to access it, Windows said that the drive was unformatted, and offered to format it for me.

[QUOTE=rcarring]Boot with your XP cd and attempt to repair from the recovery console.[/quote]
I've tried, but the console can't find any Windows installations to repair.

---

### Post by rcarring on 2006-06-04
In that case, it really does sound like the partition has been reformatted as ext2.

You will have to reinstall Windows XP.

Having said that, you now have an opportunity to create a partition for XP and one for Ubuntu.

Boot with XP CD and when it asks you to create partitions:

a) delete the existing ext2 partition
b) create a new partition sized at 50% of disk size, e.g. disk =40Gb, then create new partition of 20GB.

c) if you wish to mount XP drive in Ubuntu, chose Fat32, else chose NTFS.

d) Reinstall XP

e) When XP is working fine, reboot with Live CD.

f) In partitioner create Ubuntu drive in the freespace.

g) Follow instructions posted elsewhere for installing clean Ubuntu.

Hope this helps.

---

### Post by percy1 on 2006-06-04
You have been very helpful rcarring, thanks.

Unfortunately there is another slight complication that shows me up as a bit of a fool: there were a few files on the harddrive that I neglected to backup (although in my defence, I didn't have the spare space to do so).

Before I follow rcarring's instructions above, is there any way to recover the files on the disk? I haven't written to it in any way, and I'm reluctant to reformat until I've exhausted every other possibility.

I've found ext2 recovery tools, and I've found fat32 recovery, but I don't know enough about the file allocation table involved to be able to work out a strategy for salvaging wht I've lost.

---

### Post by rcarring on 2006-06-04
If the drive is ext2, your data has gone, it was previously fat32 or ntfs on the xp drive.

Failing that, you could try the following kludge:

On a different system connect the drive

Boot that system using the live cd

Mount the messed up drive using the live cd

If your network is up on the second machine, email the files to yourself.

What files do you think you've lost?

---

