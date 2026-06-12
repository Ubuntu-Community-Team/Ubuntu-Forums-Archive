---
title: "Is EXT4 without extents faster than EXT3?"
date: 2009-02-12
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by volanin on 2009-02-12
My Ubuntu partitions are currently formatted as EXT3.
I am considering moving my partitions to EXT4 to improve speed.

But since I dual boot Ubuntu/MacOSX and MacOSX can only read EXT2 filesystems,
I would have to mount the new EXT4 filesystems without extents support.

Is the trouble worth it?
Will it improve my performance?

---

### Post by inportb on 2009-02-12
If you want, you could convert your Linux system partition to Ext4 and keep your [shared] data partition Ext3. This way you'd be able to take advantage of faster boot and program initialization while not compromising on compatibility.

---

### Post by croxis on 2009-02-12
That is exactly what I did as well as the Windows driver can only read ext2/3 as well.

---

### Post by TheUnderTaker on 2009-02-13
Depends on what your doing

Ext4 without extents will do what ext3 does and map files with direct blocks and indirect blocks. So file deletion times will be the same. But you still get the advantages of ext4 of mutiblock allocation and delayed allocation.

---

### Post by autocrosser on 2009-02-13
I've noticed on my system with extents enabled that file transfer/deletion is much faster than with ext3--If I were you, I'd go all the way--extents will be better in the long run.

---

### Post by volanin on 2009-02-13
I have been experimenting since yesterday and went with autocrosser's approach.
The speed difference is noticeable, and I converted both system and data
partition to EXT4 with extents!

After all, who gives a **** to MacOSX?
Hehehehe!
:)

---

### Post by inportb on 2009-02-13
Heh, I guess it's time these non-native Ext drivers started supporting extents, because they'd be obsoleted soon otherwise...

---

