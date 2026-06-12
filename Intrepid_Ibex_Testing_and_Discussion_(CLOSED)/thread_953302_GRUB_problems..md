---
title: "GRUB problems."
date: 2008-10-20
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by volanin on 2008-10-20
I have a macbook.
Every macbook has, by default, a FAT32 partition as sda1.
This partition exists because of the EFI standard, and is mostly unused.
I wanted to use it, so while I was installing Intrepid today I set it to be /boot.

But then, I ran into problems while installing GRUB.
I tried to install it manually afterwards:

```
# grub

grub> root (hd0,0)
grub> setup (hd0,0)
Error 17: Cannot mount selected partition

```

Both the grub files and the linux kernel are in this partition.
But grub seems to be unable to mount the FAT32 partition and read the files.
If I do the same thing in an EXT2/3 boot partition, everything works fine.

Is this a grub limitation, or a bug maybe?
:confused:

---

### Post by volanin on 2008-10-20
I did some extra tests, and look at this:

```
grub> root (hd0,
 Possible partitions are:
   Partition num: 0,  Filesystem type unknown, partition type 0x83
   Partition num: 1,  Filesystem type is ext2fs, partition type 0x83
   Partition num: 2,  Filesystem type is ext2fs, partition type 0x83
   Partition num: 3,  Filesystem type unknown, partition type 0x83
   Partition num: 4,  Filesystem type unknown, partition type 0x83
   Partition num: 5,  Filesystem type unknown, partition type 0x83
```

But these partitions are as follows:

Partition 0: FAT32 [/boot]
Partition 1: EXT3  [/home]
Partition 2: EXT3  [/]
Partition 3: NTFS
Partition 4: SWAP
Partition 5: HFS+

And except for partitions 1 and 2, they are not type 0x83 in fdisk.
What is going on?
:confused:

---

### Post by jack_the_nimble on 2008-10-20
Hmmm.... This is interesting, I wouldn't have kept the partition fat32 if it were me.  (I would actually use it as an excuse to try out new ext4)  I noticed from the bottom of your posts that you use a custom kernel, so that would explain why you just don't redo everything.  Hmmm..... I would give SYSTEMRESCUECD a try, to see if you could move the kernel, or anything else important over to a hard drive or removable media and reinstall grub on an ext something file system.  I'm really not big on fixing boot managers, just starting over with them, however, there are those who disagree.

---

### Post by volanin on 2008-10-20
> **jack_the_nimble said:**
> Hmmm.... This is interesting, I wouldn't have kept the partition fat32 if it were me.  (I would actually use it as an excuse to try out new ext4)

Oh, I also hate this FAT32 partition...
But MacOSX requires it in order to be installed.
So I try to keep my system as standard as possible.

> I noticed from the bottom of your posts that you use a custom kernel, so that would explain why you just don't redo everything.  Hmmm..... I would give SYSTEMRESCUECD a try...

About the custom kernel, you are right.
But this custom kernel is my Hardy kernel!

When I ran GRUB, I was running it from the Intrepid LiveCD.
And to be really honest, I also downloaded and tried all LiveCDs
since Dapper 6.06, and none of them worked...

Dapper was the only one that gave me different results:

```
grub> root (hd0,
 Possible partitions are:
   Partition num: 0,  Filesystem type unknown, partition type 0xee
   Partition num: 1,  Filesystem type unknown, partition type 0x83
   Partition num: 2,  Filesystem type unknown, partition type 0x83
   Partition num: 3,  Filesystem type unknown, partition type 0x07
```

Is detected all the partition types as they as configured.
But it couldn't even detect the EXT3 filesystems.
And it couldn't read all the partitions also,
only the four primary ones in the MBR.

So I am starting to suspect that this *might* be some problem with GRUB
and the GPT partition description that EFI systems have.
(Macbooks do not use the classic BIOS)

> ...to see if you could move the kernel, or anything else important over to a hard drive or removable media...

The reason for keeping the grub files and the kernel in this first FAT32
partition is that GRUB can only read the four first MBR partitions when
it loads. So, if it could load the kernel from this first partition,
I could install linux in ANY other partition, and my system would
be a lot more flexible.

As I showed in my previous post, I have the root filesystem in sda3,
and the swap in sda5. Currently, if I temporarily nuked the swap
filesystem to try a new version of fedora, I can't boot it since
grub cannot see sda5 during load. I have to put the fedora kernel
in the sda3 partition, mixing it with the ubuntu files... not ideal.

> ...and reinstall grub on an ext something file system.

And if I temporarily nuke the FAT32 partition and reformat it as EXT3,
everything works perfectly! But as I said, I want to keep my system
as standard as possible, because MacOSX installation requires the
FAT32 to be there.

I also read reports (on Google) about grub working on FAT32 partitions.
So I am really confused about this.

> I'm really not big on fixing boot managers, just starting over with them, however, there are those who disagree.

That's no problem!
Thanks a lot for the ideas!
And sorry for the enourmous post!
:)

Does anyone else has the /boot partition as a FAT32 partition.
Does it work perfectly?

---

### Post by volanin on 2008-10-20
Ok, found the problem:

Checking the grub source code, I discovered that it hardcodes EVERY
partition as type EXT2/3 when you have a GPT partition descriptor.
So, when it tries to mount a FAT partition, it fails.

So, this is a grub bug.
In EFI systems, only EXT2/3 boot partitions will work.
:sad:

---

