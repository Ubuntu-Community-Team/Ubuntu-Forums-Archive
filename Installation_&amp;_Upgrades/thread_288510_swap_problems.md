---
title: "swap problems"
date: 2006-10-29
forum: Installation &amp; Upgrades
---

### Post by forlaf on 2006-10-29
Hello,
I wanted to make a recording studio out of a low-latency Fedora installation on my first hard drive. It's been a bit of a mess. I had Dapper on my second drive, and lost it. I believe by messing with the MBR. So, I've made a new install of Edgy on hdb.

In Edgy, if I look at the System Monitor under Resources, the "Used Swap" line shows "0 bytes of 0 bytes".

"sudo fdisk -l" looks like this:

Disk /dev/hda: 30.0 GB, 30020272128 bytes
255 heads, 63 sectors/track, 3649 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1          13      104391   83  Linux
/dev/hda2              14        3649    29206170   8e  Linux LVM

Disk /dev/hdb: 41.1 GB, 41174138880 bytes
255 heads, 63 sectors/track, 5005 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        4912    39455608+  83  Linux
/dev/hdb2            4913        5005      747022+   5  Extended
/dev/hdb5            4913        5005      746991   82  Linux swap / Solaris

It seems like /dev/hdb2 and /dev/hdb5 are two names for the same partition, and Edgy can't see hdb5. Could the Fedora install put a swap partition on a different drive? (It was installed first).

If anyone can point me where to go with this, I would very much appreciate it. This hasn't been happy computer time for me. Edgy works, but it tends to freeze up. I don't think it's using a swap. I would very much like to fix this without screwing it all up again.

Thank-you,
David

---

### Post by handy on 2006-10-30
If you have 1Gb or so of ram it questionable as to whether you even need swap?  Perhaps for your music it is more important, though I would think for lower latency you would want plenty of ram?

If you have a look with:

***Menu:* System / Administration / Gnome Partition Manager**

You can get a graphical diplay of whichever drive you select.  That may help you see if things are as you expect.

Also, if you look at:

***Menu:* System / Administration / System Monitor - Tab = Resources**

You will see if Edgy has accepted your **/swap**.

Best I can do for you, all the best... :)

---

