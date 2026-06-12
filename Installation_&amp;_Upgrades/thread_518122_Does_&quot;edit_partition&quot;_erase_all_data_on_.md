---
title: "Does &quot;edit partition&quot; erase all data on the partition?"
date: 2007-08-05
forum: Installation &amp; Upgrades
---

### Post by schrankage on 2007-08-05
It's been awhile since I've installed linux, and I was wondering if the partitioners can edit existing partitions, ie resize an ntfs partition, without destroying all the data contained on it. So is it possible to partition the free space without destroying the existing files?:confused:

---

### Post by wolfen69 on 2007-08-05
if you are really concerned about resizing, partitioning, etc. either back up or get a second drive to install ubuntu.(and unplug xp drive while installing ubuntu.)

---

### Post by Wim Sturkenboom on 2007-08-05
Yes, it is possible but **you can never rely on it**. A power failure or a little mistake and it's bye bye data.
I have succesfully resized a NTFS partition so I could install Linux on one of my boxes.

Note: Do not forget to defrag first

---

### Post by xzero1 on 2007-08-05
Yes, free space is unused, there is no file system defined on it. You may edit freespace as you like. Still, to be safe, I would backp the partition table, and any important partitions before doing so.

---

### Post by dabl on 2007-08-05
> **wolfen69 said:**
> 

 either back up or get a second drive to install ubuntu



I second the motion -- we don't need to see any more of these: [http://ubuntuforums.org/showthread.php?t=517841](http://ubuntuforums.org/showthread.php?t=517841)

However, I'm not keen on pulling the plug on one hard drive while installing Linux on the other, if you want Grub to work.  Better to make yourself a GParted Live CD, by downloading and burning the ISO from here: [http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828)

Boot the GParted CD, and review your existing partions, make sure the "boot" flag is set on the one that you mean to be the "master" for booting purposes, and plan on installing Grub there.  Usually this is the Windows boot partition -- Grub will work with that just fine. *

Make yourself three partitions -- one each for root ("/"), swap, and home ("/home).  For Ubuntu, 8GB for root is way plenty, 1GB for swap is more than I've seen used by twice, and the rest of it can be your home partition for your data.

Study up on some of the fine points here: [http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

When you're done partitioning, then you can boot your Ubuntu Alternate Install CD, use VGA/text mode, and simply assign your partitions to the 3 mount points that I listed above, and let it install Grub on the partition that you have the "boot" flag set on, and life should be pretty good.  :guitar:

* If it's VISTA, better search for special issues dual booting with Vista.

---

