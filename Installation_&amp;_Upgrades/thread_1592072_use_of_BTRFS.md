---
title: "use of BTRFS ?"
date: 2010-10-10
forum: Installation &amp; Upgrades
---

### Post by wpshooter on 2010-10-10
I am about to setup a computer with Maverick.

This will be for experiment use only, there will be nothing of any critical nature on it.

Should I consider using the BTRFS, yes or no ?

What would be the advantages/disadvantages (if any) on using it as opposed to EXT4 ?

Thanks.

---

### Post by efflandt on 2010-10-10
If you have an expendable drive with no essential data (or backed up regularly) and 10.10 is working stable for you fine otherwise, go for it.  Your input would help whoever is developing it determine if there are any problems with it.  You will need a separate /boot partition because grub cannot read it yet.

From [https://btrfs.wiki.kernel.org/index.php/Main_Page](https://btrfs.wiki.kernel.org/index.php/Main_Page)

> Note that Btrfs does not yet have a fsck tool that can fix errors. While  Btrfs is stable on a stable machine, it is currently possible to  corrupt a filesystem irrecoverably if your machine crashes or loses  power on disks that don't handle flush requests correctly. This will be  fixed when the fsck tool is ready. 

---

### Post by wpshooter on 2010-10-10
> **efflandt said:**
> If you have an expendable drive with no essential data (or backed up regularly) and 10.10 is working stable for you fine otherwise, go for it.  Your input would help whoever is developing it determine if there are any problems with it.  You will need a separate /boot partition because grub cannot read it yet.

From [https://btrfs.wiki.kernel.org/index.php/Main_Page](https://btrfs.wiki.kernel.org/index.php/Main_Page)

Thanks.

Yes, I had already read that the FSCK was not yet ready.

Any idea as to when that might be available or where to find out about its projected availability date ?

---

### Post by DarkRedman on 2010-10-10
> **efflandt said:**
> You will need a separate /boot partition because grub cannot read it yet.

From [https://btrfs.wiki.kernel.org/index.php/Main_Page](https://btrfs.wiki.kernel.org/index.php/Main_Page)


How much place the /boot partition needs ?!

---

### Post by gruffy-06 on 2010-10-23
Usually I recommend having at least 250MB. You might want more if you are interested in compiling your own kernel.

---

