---
title: "Merge free space with primary partition"
date: 2006-10-20
forum: Installation &amp; Upgrades
---

### Post by livingtarget on 2006-10-20
Right I've got harddrive B, which contains 1 FAT32 partition, a linux swap partition, some rather large and empty ext3 10gb space and a small ext3 2gb partition with "/" on it. Now I want to merge the 10 with the 2 for convenience. How do I go about doing this, without reinstalling Ubuntu?

Would mounting the second drive as "/" work at all or is this better avoided?

---

### Post by reacocard on 2006-10-20
If the / partition is right before the 10GB, you can just use GParted to delete the 10GB partition and expand the 2GB into the empty space. If the 10GB is before the 2GB, you can't. It is not possible to extend an ext3 partition backwards.

---

### Post by livingtarget on 2006-10-20
Alright thanks for the info, looks like I'll be doing a reinstall whenever I can be bothered to do so. :KS

---

### Post by dcstar on 2006-10-21
> **livingtarget said:**
> Right I've got harddrive B, which contains 1 FAT32 partition, a linux swap partition, some rather large and empty ext3 10gb space and a small ext3 2gb partition with "/" on it. Now I want to merge the 10 with the 2 for convenience. How do I go about doing this, without reinstalling Ubuntu?

Would mounting the second drive as "/" work at all or is this better avoided?

You may be able to use **partimage** to save and restore the partitions.

Use it to copy the "/" partition you want to save (somewhere else where it fits), then delete both the partitions and create a single one, and then restore the saved partition there.

---

### Post by H.E. Pennypacker on 2006-10-22
> **reacocard said:**
> If the / partition is right before the 10GB, you can just use GParted to delete the 10GB partition and expand the 2GB into the empty space. If the 10GB is before the 2GB, you can't. It is not possible to extend an ext3 partition backwards.

Has this been purposely decided upon by whoever made the harddrive?  I would like to know why I can't merge two partitions, just because the empty partition comes after the used partition.  It's ridiculous, because I don't want someone else telling me what I can't do.

I hope this is not an effort by someone or something to keep people from merging partitions, as probably has been done with limiting harddrives to four main partitions.

---

### Post by reacocard on 2006-10-22
> **H.E. Pennypacker said:**
> Has this been purposely decided upon by whoever made the harddrive?  I would like to know why I can't merge two partitions, just because the empty partition comes after the used partition.  It's ridiculous, because I don't want someone else telling me what I can't do.

I hope this is not an effort by someone or something to keep people from merging partitions, as probably has been done with limiting harddrives to four main partitions.

It's not the harddrive, it's the filesystem. ext3 just doesn't take well to being moved backwards on the disk. nor do most other modern filesystems, for that matter.

---

### Post by H.E. Pennypacker on 2006-10-22
> **reacocard said:**
> It's not the harddrive, it's the filesystem. ext3 just doesn't take well to being moved backwards on the disk. nor do most other modern filesystems, for that matter.

I'll have to look for a filesystem that will allow that, and after having merged the partitions, convert the merged partition into ext3.

---

### Post by reacocard on 2006-10-22
> **H.E. Pennypacker said:**
> I'll have to look for a filesystem that will allow that, and after having merged the partitions, convert the merged partition into ext3.

The only one I know of that allows it is fat32, and changing filesystems usually requires deleting all the data on the partition involved.

---

### Post by az on 2006-10-22
> **H.E. Pennypacker said:**
> I would like to know why I can't merge two partitions, just because the empty partition comes after the used partition.  It's ridiculous, because I don't want someone else telling me what I can't do.


No.  It has to do with a limitation in parted (the backend program that does the work) and the linux kernel.  It writes on-way.  To move the starting point of a partition is not feasable.

In this case, though, since the / partition is much smaller than the free space, a partition can be created using the free space, the small partition's filesystem can simply be copied onto the new partition and then deleted.  The new big partition can then be extended to use the newly freed 2GB free space.

It has nothing to do with the filesystem.

> **H.E. Pennypacker said:**
> 
I hope this is not an effort by someone or something to keep people from merging partitions, as probably has been done with limiting harddrives to four main partitions.

The primary partitions are just a few bytes on the MBR.  There is not enough space to permit more primary partitions.  That's pretty irrelevant since you can have more than enough extended partitions.

---

