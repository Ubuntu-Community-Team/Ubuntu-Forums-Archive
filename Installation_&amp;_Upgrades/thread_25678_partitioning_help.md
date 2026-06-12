---
title: "partitioning help"
date: 2005-04-10
forum: Installation &amp; Upgrades
---

### Post by rum beverage on 2005-04-10
recently i was dual booting with following setup:

hda1 - ntfs (installation of windows xp)
hdb1 - ntfs (data drive)
hdb2 - ext3 (installation of ubuntu)
hdb3 - swap

i've recently cleared out the windows install and would like to repartition everything to just accomodate the ubuntu installation without completely blowing it away.  so basically i'm looking to see how to go about doing this and also recommendations for partitioning and mount points.

edit: oh i forgot to mention, the disks are as follows hda (40gb 7200 rpm ata133) hdb (80gb 7200 rpm ata100)

---

### Post by Nis on 2005-04-10
Not sure if you'll be able to repartition with out "blowing away" your Ubuntu installation but here's my suggestions.
swap and / (root) go on hda
/home goes on hdb to make it easy to dist-upgrade and keep settings

I don't bother splitting up any more but some people suggest having a small (50 MB) /boot partition, and if you're running a server putting /var (or is it /tmp) on a separate partition will prevent server stuff from going wild and occuping your space.

---

### Post by az on 2005-04-11
You will not need to blow anything away, just move it around.  Create your destination partition and move your setup there.  Or keep it the way it is and mount your partitions/drives in your fstab.  It is up to you.
What do you want to do?  One great big partition, or several ones?  There is no one good answer.

---

### Post by rum beverage on 2005-04-11
well, as suggested above i was hoping to move / to hda and having the /home directory on hdb sounds like a good idea...so is this possible to do without damaging the mbr?

---

### Post by az on 2005-04-11
Of course.

Any partitionner can do this.  The Gnu partitionner is called parted and there are several frontends to it.  You must unmount the drives first, so it should be run from a ramdisk (knoppix, Ubuntu live or the ubuntu installer partitionner)

---

### Post by rum beverage on 2005-04-11
ok and what about grub...where can i modify this

i'm only skeptical because i know i've had issues with the mbr before and i really want to make sure it stays in tact

---

### Post by rum beverage on 2005-04-11
wondering if anyone could actually give a little more detail instructions on how to go about doing this?

---

### Post by rum beverage on 2005-04-12
[QUOTE=rum beverage]wondering if anyone could actually give a little more detail instructions on how to go about doing this?[/QUOTE]
 bump

---

