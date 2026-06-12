---
title: "installing windows 8. need to increase size of boot partn using gparted"
date: 2012-12-09
forum: Installation &amp; Upgrades
---

### Post by yahuggn on 2012-12-09
how does one resize the boot partition to install win 8? i have  a 30 gb boot ntfs. all other partitions are fat32 on my 750 gb hdd. so not having partition magic in win xp...i went to gparted in linu and reduced the size of some of the fat 32 partitions ...and now i have some unallocated space which i would like to add to the c:\ drive such that it increases in size and allows me to install win 8. but right now. in gparted. it only allows me to reduce the size of the 30 gb boot ntfs partition...not increase it.
 

 help!
 

 [[IMG]http://img163.imageshack.us/img163/9097/gpartedscreenshot.png[/IMG]]("http://imageshack.us/photo/my-images/163/gpartedscreenshot.png/")
 

 Uploaded with [ImageShack.us]("http://imageshack.us")

---

### Post by darkod on 2012-12-09
Why so many fat32 partitions, and why fat32 first of all? Ubuntu can read ntfs just fine so it's better the shared partitions to be ntfs.

You can't expand sda1 now because the unallocated space you created is not next to it. The Gparted screen shows it best. You can't expand a partition when the unallocated space you want to use is on the other side of the disk, right?

Right now it looks like quite a bit of mess. I would seriously consider moving the data from the shared partitions to an external hdd temporarily, then deleting all of them, shrinking sda3 from the FRONT, and that will create available space to expand sda1.

If you don't want to reorganize the whole hdd right now, what you need to do is:
1. Boot into live mode with the ubuntu session so that you can work with the partitions. Right now you can see the ubuntu partitions are mounted and locked, also sda3 because it's holding them.
2. Open Gparted in live mode, right click sda11 and select Swapoff. That should make all keys symbols go away.
3. Shrink sda5 from the FRONT for 20GB for example. That will make the unallocated space to appear before sda5.
4. Shrink sda3 from the FRONT so that the unallocated space "goes out" of sda3.
5. Expand sda1 with that space.

I would recommend to do the shrink/expand as separate operations, not all at once. Shrink sda5, execute that change and let it finish. Shrink sda3 and execute it also. Then expand sda1.

---

