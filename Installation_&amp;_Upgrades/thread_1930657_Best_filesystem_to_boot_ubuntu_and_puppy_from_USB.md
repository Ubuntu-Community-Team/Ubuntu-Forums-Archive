---
title: "Best filesystem to boot ubuntu and puppy from USB"
date: 2012-02-24
forum: Installation &amp; Upgrades
---

### Post by Ampsheep on 2012-02-24
whats the best file sytem to use when you booting Ubuntu or puppy linux(live USB)
on both Mac and Windows pc`s?

---

### Post by Ampsheep on 2012-02-26
Bump

---

### Post by Retsuzai on 2012-02-26
Linux, Windows and Mac all have their own way of doing things. The file system itself really does not even matter.

Linux will set its own file system up in its partition or temporarily in a *live* case and windows will be using FAT or NTFS depending on drive size.

I Have Ubuntu and Windows on the same Drive both with their own partitions and they can recall information form each other just fine.

I hope this helps if not if you can elaborate a bit more it would be helpful.

-ret

---

### Post by ottosykora on 2012-02-27
> **Ampsheep said:**
> whats the best file sytem to use when you booting Ubuntu or puppy linux(live USB)
on both Mac and Windows pc`s?

the use of mac or windows is here irelevant as you are going to boot from the live usb system. You can also have no hard drive in your computer, it will be the same.

Linux today uses ext4 in general and this is what is relevant. You can use ext3 also, but ext4 might work slightly faster.

---

### Post by James Willis on 2012-02-27
I have Ubuntu and Puppy installed on a USB flashdrive using ext4 which is working great.  Since it is used on a Windows laptop, it also has a FAT32 partition to make it easy to swap files with Windows.

---

