---
title: "Will Karmic Koala install convert ext3 to ext4?"
date: 2009-10-04
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Mark_in_Hollywood on 2009-10-04
Will upgrading to Karmic from Jaunty automatically change ext3 to ext4?

---

### Post by nhasian on 2009-10-04
it will not do it automatically.  although you can manually convert the EXT3 partition to EXT4 yourself, you will not get all the speed improvements unless you do a fresh install.  also be advised that the older grub doesnt work with EXT4 boot partitions so you would also have to upgrade your grub to grub2 manually as upgrading to karmic doesnt do it for you.

all in all i highly recommend backing up your data and doing a fresh install with karmic when it comes out.  it would be much easier.

---

### Post by LewRockwell on 2009-10-04
> **nhasian said:**
> it will not do it automatically.  Although you can manually convert the ext3 partition to ext4 yourself, you will not get all the speed improvements unless you do a fresh install.  Also be advised that the older grub doesnt work with ext4 boot partitions so you would also have to upgrade your grub to grub2 manually as upgrading to karmic doesnt do it for you.

All in all i highly recommend backing up your data and doing a fresh install with karmic when it comes out.  It would be much easier.

+ 1

.

---

### Post by t0p on 2009-10-04
There's a HOWTO on converting an ext3 filesystem to ext4 [here]("https://help.ubuntu.com/community/ConvertFilesystemToExt4").  Make sure you backup everything of importance before embarking on this.

---

### Post by Anubis on 2009-10-04
:lolflag:

---

### Post by Gourgi on 2009-10-04
> **t0p said:**
> There's a HOWTO on converting an ext3 filesystem to ext4 [here]("https://help.ubuntu.com/community/ConvertFilesystemToExt4").  Make sure you backup everything of importance before embarking on this.

if you can backup everything somewhere else then it is better to just delete the partition, format it as ext4 and restore the data.
their is no point at converting if you can reformat.

---

### Post by FuturePilot on 2009-10-04
> **nhasian said:**
>  also be advised that the older grub doesnt work with EXT4 boot partitions 

Actually Grub was patched for Ext4 support in Jaunty.

---

