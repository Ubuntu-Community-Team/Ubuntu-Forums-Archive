---
title: "Dual boot partition"
date: 2010-05-04
forum: Installation &amp; Upgrades
---

### Post by paynek716 on 2010-05-04
I currently have a dual boot with Karmic and Vista. Will be doing a fresh install of Lucid. I plan to add a data partition to my hard drive to share data between OS's.

Does it matter which partitions are primary or extended? Here is my planned partition. It is 500GB so space is not an issue.
[LIST]
[*]50GB NTFS Vista
[*]2GB swap
[*]50GB root
[*]100GB data
[*]298GB home
[/LIST]

---

### Post by chejrw on 2010-05-04
The Windows primary partition (aka Drive c: ) must be on a primary partition, as must /root/

Other than that, it doesn't matter.

---

### Post by windfix on 2010-05-05
Can the /home partition be NTFS in order for Windows to access your files?

---

### Post by chejrw on 2010-05-05
> **windfix said:**
> Can the /home partition be NTFS in order for Windows to access your files?

I don't see why not.  It's a little unconventional, but as long as it's properly documented in fstab it should work.

---

### Post by srs5694 on 2010-05-05
First, Linux does *not* require *any* of its partitions to be primary. In fact, you can install Linux on a disk that has *no primary partitions at all.* That said, most distributions, including Ubuntu, will create at least one primary partition when they're given a completely blank disk and told to auto-partition it.

Second, Linux's /home partition *should **not*** be NTFS. Although most files would be fine that way, a few programs do create files in users' home directories with features that aren't supported by NTFS, so NTFS is at best a risky choice for /home. You can, however, mount a shared-data partition in /home or one of its subdirectories (such as your own user home directory). For instance, if your username is paynek, you could mount an NTFS shared-data directory at /home/paynek/shared; or if your system supports multiple users, you might prefer to mount it at /home/shared, /mnt/shared, or /shared, to name just a few possibilities.

---

### Post by paynek716 on 2010-05-05
I was just concerned if it mattered _what_ partitions were extended, not primary. I will repartition the /home partition into an extended partition, part of it /home EXT4 and part of it /data NTFS.

Thanks to all for the help.

---

