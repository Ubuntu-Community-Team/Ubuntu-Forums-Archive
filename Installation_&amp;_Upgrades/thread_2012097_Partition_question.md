---
title: "Partition question"
date: 2012-06-28
forum: Installation &amp; Upgrades
---

### Post by Lfc_Gazza on 2012-06-28
Hello
It has been a couple of years since i last used Ubuntu and i want to start using it again. I am currently trying to install it so i have both Windows 7 and Ubuntu on the hard drive. I am stuck on the partition bit as i don't know what to do next and don't want to accidentally knock off windows 7 and all my files.
On my screen i have 3 partitions in the table thing

/dev/sda
/dev/sda1 ntfs Size: 104mb Used: 35mb
/dev/sda2 ntfs Size: 499999mb Used: unknown

So what do i do next?

Thanks

---

### Post by darkod on 2012-06-28
Looks like your win7 C: partition is taking the whole disk (except the small 100MB partition that doesn't show in Computer in win7, which is /dev/sda1).

If C: takes the whole disk, first you need to shrink it to make unallocated space for ubuntu. In win7 open Disk Management and shrink the win7 partition for as much as you want to allocate to ubuntu.

Restart win7 few times in case it wants to do any disk checks after the shrink. And leave the space as unallocated, DO NOT create ntfs partition from windows since ubuntu doesn't install on ntfs.

After that is done, you can install in any way you like, either with the auto method, or the manual method using Something Else if you want to create a more specific layout.

---

