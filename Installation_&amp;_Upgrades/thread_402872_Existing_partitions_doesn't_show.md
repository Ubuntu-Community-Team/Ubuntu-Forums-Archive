---
title: "Existing partitions doesn't show"
date: 2007-04-06
forum: Installation &amp; Upgrades
---

### Post by monti on 2007-04-06
I've got a Dell Inspiron 500m with Windows XP and Debian testing installed, working flawlessly.  

I thought I'd replace Debian with Ubuntu 7.04 beta, but it seems like a difficult task for this computer.  When I arrive at the partition editor (both in the GUI and the alternative installer), the whole hard drive shows up as one large unallocated space of 80GB (which is the size of my drive).

The fdisk command in Ubuntu Live and Debian shows the partitions.  Windows XP shows the partitions.  Why doesn't the Ubuntu installer see them?  Does anyone have a clue?

---

### Post by Najand on 2007-04-06
Use Gnome Gparted Live CD to partition it first and then install ubuntu on it.

---

### Post by monti on 2007-04-06
Thanks for the fast reply!

I am not really trying to create new partitions, as my existing partitions for Debian Linux should be good enough.

fdisk -lu shows:

```
Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1              63       96389       48163+  de  Dell Utility
/dev/hda2   *       96390    61448624    30676117+   7  HPFS/NTFS
/dev/hda3        61448625   154175804    46363590   83  Linux
/dev/hda4       154175805   156280319     1052257+  82  Linux swap / Solaris
```

while gparted shows a single disk without partitions, the same way that the Ubuntu Installer did:

```
/dev/hda (!)    fat16    74,53 GiB
```
When I open the extended information on the disk, gparted also says *"Unable to read the contents of this filesystem!  Because of this some operations may be unavailable.  Did you install the correct plugin for this filesystem?"*

I see the same problems listed in [http://ubuntuforums.org/showthread.php?t=188532](http://ubuntuforums.org/showthread.php?t=188532) and [https://launchpad.net/ubuntu/+source/gparted/+bug/48412](https://launchpad.net/ubuntu/+source/gparted/+bug/48412), but the solutions there doesn't seem to apply for me.  As far as I can see, the partitions aren't overlapping, and most tools (except for gparted and ubuntu install) detect the partitions as they should.

---

### Post by monti on 2007-04-12
It seems libparted is to blame:

[http://parted.alioth.debian.org/cgi-bin/trac.cgi/ticket/14](http://parted.alioth.debian.org/cgi-bin/trac.cgi/ticket/14)

[EDIT:] It seems I probably can work around my problem by using TestDisk: [http://ubuntuforums.org/showthread.php?p=2486121#post2486121](http://ubuntuforums.org/showthread.php?p=2486121#post2486121) .  I haven't tried it yet, though.

---

