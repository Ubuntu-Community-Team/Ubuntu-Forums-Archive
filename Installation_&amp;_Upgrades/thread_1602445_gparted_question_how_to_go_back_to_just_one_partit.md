---
title: "gparted question how to go back to just one partition from 3"
date: 2010-10-21
forum: Installation &amp; Upgrades
---

### Post by shantiq on 2010-10-21
i had three part to my hard drive

lucid lynx / linuxmint and meerkat


i have taken out the 1st 2 and only want meerkat now

check attached image


now it is not letting me move meerkat into the unallocated and i do not understand why    must be simple but i have not used gparted for a while


any idea?

---

### Post by lechien73 on 2010-10-21
The problem is that your Meerkat installation is in an extended partition, rather than a primary partition.

I have seen it done before where you can change an extended partition to a primary one from the command line, by booting from a Live CD and overwriting the partition table.

I can't see anything in GParted that would let you do that, though - although maybe I'm just not looking properly.

I think the best thing would be to make a complete backup of your Meerkat partition, wipe the entire disk, and then restore your backup. Unless you're feeling brave and want to try the command line route :) - even then, you will want a full backup of your data in case things go horribly wrong!

---

### Post by jerrrys on 2010-10-21
couldn't you just do a partition to partition clone with something like clonezilla or ddrescue?

---

### Post by Lazaruss on 2010-10-21
Grow the extended partition then resize the meerkat partition? (I might be wrong here)

What effect does it have for everything to be in an extended partition?

---

### Post by shantiq on 2010-10-21
> **lechien73 said:**
> The problem is that your Meerkat installation is in an extended partition, rather than a primary partition.



well spotted    how the heck did i do that? idiot that i am
i see why 



well is there a way out?    it might mean reinstall at some stage

i still have 200GB spare so no big problem as yet but i like things tidy and would like the whole disk in one place under the meerkat


let us see if any more info appears but lechien thanx for your dogs bollocks spotting quality
:KS   dear how did i even do that?

---

### Post by perspectoff on 2010-10-21
The most painfree way is not to delete or reorder any partitions (which changes things in the partition table as well as UUIDs, sometimes).

Merely reformat the partitions you no longer want to use (which will erase their contents) and then shrink them to their smallest possible size (using GParted).

Then expand ("grow") the partition of Meerkat.

If, as I understand, Meerkat is in a logical partition, then expand the extended partition first. Then expand the Meerkat logical partition so that it fills whatever space has now become available within the extended partition.

(There are many other solutions, but by not changing the order or types of partitions, you won't screw up your bootloader in its effort to find the partitions.)

PS, There is nothing wrong with having your Ubuntu installation in a logical partition in the extended partition. (In fact, in newer consumer computers distributed with 3 NTFS partitions, installing Ubuntu in a logical partition within the extended partition is the only way to achieve a dual-booting computer (aside from installing within Windows using Wubi, deleting one of the NTFS partitions, or running in a virtual machine in Windows, all of which are inferior solutions IMO).)

Specifically looking at your GParted screencapture, though, I'll guess what's going on in your computer.

You have a bootloader in /dev/sda1 (since there is only 50 Mb used, which is about what most bootloader files require).

You can shrink this partition to about 100 Mb safely.

You then have a lot of free space (which I'll wager used to belong to a Windows installation). You can grow the extended partition to use all this free space.

You only need one linux-swap partition on any computer, so you can safely delete one of them (the /dev/sda5 one, since it is not being used). However, if you want to avoid changing the partition numbering scheme, merely shrink /dev/sda5 to 10 Mb (or something similarly small). It won't hurt anything.

Also, a 6 Gb linux-swap partition is overkill. It is doubtful that any swap partition greater than 2 Gb does any good. You can shrink the remaining swap-partition (/dev/sda7) that remains to 2 Gb (although you can only do that using GParted from a LiveCD).

In fact, you can't change the partition of the OS you're running from within that OS, either. (The lock symbols mean you can't change the partitions because you are actively using them.)

Since you only have one OS left on your computer, you will have to run GParted while booted into a LiveCD (either the Ubuntu LiveCD (System -> Administration -> GParted) or the GParted LiveCD itself).

Now, it is safe to delete any partitions that are following the partition you wish to keep. On your computer, your Ubuntu partition is /dev/sda6, and /dev/sda7 is used as the swap. You can delete anything after /dev/sda7 safely (i.e. /dev/sda8). it appears you have already done this, since there is lots of "unallocated space").

So now move the partitions around so that the unallocated space within the extended partition is touching the dev/sda6 partition. (In other words, move the /dev/sda7 partition to the right so that the two unallocated spaces (6.99 Gb and 4.00 Gb) become contiguous as one 10.99 Gb unallocated space and are situated right after the /dev/sda6 partition).

When you expand the extended partition so that it occupies the 100.49 Gb unallocated space, that unallocated space will then show up as unallocated space either at the end of the extended partition or at the beginning (I'm not sure which).

If it shows up in the extended partition immediately preceding the /dev/sda6 partition, you can merely expand the /dev/sda6 to include it at the same time you expand the /dev/sda6 partition to include the 10.99 Gb unallocated free space.

However, if the 100.Gb unallocated free space is moved to the end, then again move the /dev/sda5 and /dev/sda6 partitions to the right so that the 100.49 Gb unallocated space is also contiguous with the 10.99 Gb free space, giving you 111.39 Gb unallocated space. Now you can grow your /dev/sda6 partition by 111.39 Gb.

---

### Post by kansasnoob on 2010-10-21
A couple of questions:

Does Ubuntu reboot OK right now? 

What's up with that small "media" partition on sda1? Is that data storage? Only 52MiB stored? What's there?

If the answer to the first question is yes then please post the output of:

```
cat /etc/fstab
```

And also:

```
free
```

You are rather painting yourself in a corner and if you plan on booting multiple distros in the future you need a plan :)

---

### Post by kansasnoob on 2010-10-21
> (There are many other solutions, but by not changing the order or types of partitions, you won't screw up your bootloader in its effort to find the partitions.)

+1!

All kinds of problems can be encountered! Device designations and/or UUID's can/will change. While this can all be solved it's NOT really easy the first time around the block :)

---

### Post by perspectoff on 2010-10-21
> **kansasnoob said:**
> +1!

All kinds of problems can be encountered! Device designations and/or UUID's can/will change. While this can all be solved it's NOT really easy the first time around the block :)

Exactly. Those are the problems that occurs whenever you change the order or types of the partitions. That's exactly why I'm advocating not changing the partition order. Merely resizing partitions does not change their UUIDs.

Further, manipulating any partitions after the one(s) you are using has no affect on the UUID of the partition you are using, either.

Since this user has already deleted the OS's, and they happened to be in partitions following his Ubuntu partition, he is lucky.

The problem with Clonezilla or other partition-copying scheme is that UUID control becomes tricky.

---

### Post by kansasnoob on 2010-10-21
> Merely resizing partitions does not change their UUIDs.

With the exception of SWAP it seems like. Sometimes it does, sometimes it doesn't. I've never really figured out why :confused:

Simply "copying" SWAP never seems to change the UUID.

What I'm most concerned with there is that they have a "mounted" media partition which is the only primary. Due to it's size I wonder if it wasn't used to "house" part of the boot files or something.

It's a very odd partitioning arrangement :(

---

### Post by shantiq on 2010-10-22
ok sorted !!!


the obvious thing to do after le chien 's observation that the problem was that  meerkat was installed in an extension and not the primary partition




was to go back and first extend the primary partition ( actually not primary still extended but i mean one up from the one highlighted in the screenshot 362.59gb )into the unallocated space then extend the extension which contained meerkat into that space

so the first step took 5 seconds


and the second 5 hours    



so easy really once it was spotted that the OS has been stored in an extension

---

### Post by lechien73 on 2010-10-22
Good stuff...glad you have it sorted. The whole partitioning thing can be a bit of a minefield.

> thanx for your dogs bollocks spotting quality

I like that :grin:

---

