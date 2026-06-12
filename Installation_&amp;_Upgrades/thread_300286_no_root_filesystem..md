---
title: "no root filesystem."
date: 2006-11-15
forum: Installation &amp; Upgrades
---

### Post by gammyhand on 2006-11-15
I have finally got ubuntu past the partitioner stage by just leaving it chugging through the I/O errors. However once I had defined the partitions it started formatting and came up with "no root filesystem defined" and I don't know what to do about that. I told it to make the main partition ext3 and bootable. 

I can only run the live cd now of edgy as it has knackered my hoary install.

I have just done fsck and fdisk -l on my drives and these are the results:

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       12158    97659103+  83  Linux
/dev/hda2           12159       30515   147452602+   5  Extended
/dev/hda5           12159       30515   147452571    7  HPFS/NTFS


fsck 1.39 (29-May-2006)
e2fsck 1.39 (29-May-2006)
/dev/hda1: clean, 11/12222464 files, 416364/24414775 blocks

fsck 1.39 (29-May-2006)
e2fsck 1.39 (29-May-2006)
fsck.ext2: Attempt to read block from filesystem resulted in short read while trying to open /dev/hda2
Could this be a zero-length partition?

fsck 1.39 (29-May-2006)
fsck: fsck.ntfs: not found
fsck: Error 2 while executing fsck.ntfs for /dev/hda5

---

### Post by taurus on 2006-11-15
Did you tell the installer to mount /dev/hda1 on / and format it as ext3?

---

### Post by gammyhand on 2006-11-15
I didn't check the mount point to be honest but I definitely told it to use ext3. I presumed the default mount would be /

Any other suggestions if that doesn't work so I can try them all at once.

Thanks for the help.

---

### Post by taurus on 2006-11-15
Just make sure you tell the installer to mount /dev/hda1 to / and format it as ext3 since /dev/hda5 is your swap...  That should do it.

---

### Post by gammyhand on 2006-11-15
> **taurus said:**
> Just make sure you tell the installer to mount /dev/hda1 to / and format it as ext3 since /dev/hda5 is your swap...  That should do it.

hda5 is a 150gb ntfs drive that has all my data on so I can't lose that! Will give it a go now.

---

### Post by gammyhand on 2006-11-15
Thanks Taurus :) I finally have edgy installed! Now to get wi-fi working so I am not hunched on the floor in the hall (near the router).

---

