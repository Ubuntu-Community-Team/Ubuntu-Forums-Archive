---
title: "Installing Ubuntu 10.10 on Eeepc without deleting recovery f9?"
date: 2011-03-06
forum: Installation &amp; Upgrades
---

### Post by tatsvill on 2011-03-06
Im new to Ubuntu and can't understand the whole /dev/sda stuffs ntfs limitation etc.

So i kinda need a little help here.

I have a 1005ha eepc notebook. it has 4 partition on it.
sda1 ntfs 77.4gb
sda2 ntfs 77.4gb
sda3 fat32 5.2gb
sda4(unknown) 49.4mb

Now my question is, how do i install properly ubuntu w/o killing the f9 recovery mode of eeepc. Cuz incase i want to revert back to windows i can just hit F9 at start up.

I want to use the 1st partition as my ubuntu OS then second partition as my extra storage. But i dont know how to set it properly.

Should i first change the SDA2 from ntfs to ext3 or 4? or fat 32 file system?

then click install now to sda1 ntfsto install the linux and delete the windows xp?

What is the Swap part in the partition? do i need it?

if i convert the sda2 to ext3 will it still be just the same as fat32? just copy paste stuff there?

Sorry for the noob questions. hehe

---

### Post by dabl on 2011-03-06
A hard disk drive (or SSD) can only have a maximum of 4 primary partitions, and so you are already maxed out.  The only way to have more partitions on that drive is to first delete one of the existing 4, leaving 3, and then add a new partition that is an "Extended" type, rather than primary.  Within an extended partition, you can have multiple logical partitions, within the limits of your total drive capacity, of course.

That's high-level, I know.  You have a decision to make, before dealing with "step by step".  :)

---

### Post by tatsvill on 2011-03-07
Yeah, what i would like to happen is that

my 1st partition(whre windows is loaded) is to be replaceed with a clean install of ubuntu, then the 2nd partition is soo i could store files. I was wondering is that the 2nd partition is in NTFS, and i think ubuntu cant read ntfs, making the 2nd partition unusable? 

as for the 3rd partition, I THINK that is where windows recovery is, so i dont wanna touch it. hahah

Soo what is the step by step in reformatting the 1st partition from windows to Ubuntu, and making the 2nd partition  as extra storage?

Do i still need that "Swap" thing?

---

### Post by Mark Phelps on 2011-03-07
Whenever I see two NTFS partitions exactly the same size, I suspect that the PC is using a RAID setup.  You need to confirm this before you make ANY changes to the partitions.  Otherwise, you run the risk of losing ALL your data in the process.

---

### Post by dabl on 2011-03-08
Mark Phelps is right -- if those first two partitions are in a RAID, then your first task is to make a full backup of all your data within both of them.


> **tatsvill said:**
> Yeah, what i would like to happen is that

my 1st partition(whre windows is loaded) is to be replaceed with a clean install of ubuntu, then the 2nd partition is soo i could store files. I was wondering is that the 2nd partition is in NTFS, and i think ubuntu cant read ntfs, making the 2nd partition unusable? 



No, Ubuntu will can read and write data on NTFS partitions.  However, if you don't have a Windows OS to boot, what is the point of have _any_ NTFS partitions on that computer?

> 
as for the 3rd partition, I THINK that is where windows recovery is, so i dont wanna touch it. hahah


Yes, that's fine -- just leave it alone.

> 
Soo what is the step by step in reformatting the 1st partition from windows to Ubuntu, and making the 2nd partition  as extra storage?


After the full data backup, boot your Live CD that has GParted on it, and delete the first partition.  Click "Apply" and it will be done.  In the space where the first partition was, it will say "unallocated".

Now, the strategic question is, do the sizes of those first two partitions still make sense, given the new OS?  Ubuntu would be very happy to run in 15GB or 20GB of space, even allowing for the occasional downloaded DVD or CD ISO image and lots of user data files. So maybe what you want to do is make a new ext4 partition of 20GB in the unallocated space, and then resize the second partition to be a larger (~134GB) data partition, and change the filesystem to ext4 (or leave it NTFS if you need that).

> 
Do i still need that "Swap" thing?

You can live without it, _if_ you never intend to do memory-intensive things like encoding videos, and _if_ you never need to "hibernate" or suspend to disk.  Give the "ifs", I'd recommend making a swap partition that is 1.1X the size of your computer's memory.  That way you never have to think about it.

---

### Post by tatsvill on 2011-03-11
@dabl

Thanks! Answered all my questions. I'll reformat my pc to ubuntu as soon as i can. Thanks for the info!

---

