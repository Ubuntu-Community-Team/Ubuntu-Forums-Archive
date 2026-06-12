---
title: "partition not formatted = can't mount"
date: 2006-10-07
forum: Installation &amp; Upgrades
---

### Post by GStubbs43 on 2006-10-07
[FONT=Times New Roman]Hi all, I had a partition on my computer that had all of my stuff on it that I really don't want to lose... something happened when I installed Ubuntu and now it says that partition is unformatted, which means I can't mount it and get all of my files. Is there a way to get these files and not format the partition? :confused: Thanks! [/FONT]

---

### Post by Kateikyoushi on 2006-10-07
If you copy this to a terminal we will see what is the current state of your harddisks.

```
sudo fdisk -l
```

---

### Post by GStubbs43 on 2006-10-07
```


Disk /dev/hda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device   Boot      Start        End      Blocks           Id     System
/dev/hda1   *           1            3972    31905058+  83    Linux
/dev/hda2            4663        4864     1622565        5  Extended
/dev/hda3            3973        4662     5542425       83  Linux
/dev/hda5            4663        4864     1622533+    82  Linux swap / Solaris

Partition table entries are not in disk order

```

---

### Post by GStubbs43 on 2006-10-07
/dev/hda3 is the one I need.

---

### Post by Kateikyoushi on 2006-10-07
Was it an ext3 partition before the install ?

---

### Post by GStubbs43 on 2006-10-07
I believe it was. It might have been FAT32, but I think it was ext3.

---

### Post by GStubbs43 on 2006-10-07
Sorry to bump my own thread, but I need some help on this, there is some stuff I really need on it. :(

---

### Post by GStubbs43 on 2006-10-07
anyone? :confused:

---

### Post by trash on 2006-10-07
exactly the same thing happened to me in Dapper, just at the same time i started to get I/O errors on boot. I tried a few things to rescue it but eventually I deleted the partition and the I/O errors vanished.
Not saying you should delete it.. just that it happened to me too, perhaps somebody will have an answer for you.

---

### Post by GStubbs43 on 2006-10-07
> **trash said:**
> exactly the same thing happened to me in Dapper, just at the same time i started to get I/O errors on boot. I tried a few things to rescue it but eventually I deleted the partition and the I/O errors vanished.
Not saying you should delete it.. just that it happened to me too, perhaps somebody will have an answer for you.


ah! I have some stuff on there that I would really like to have, like a month of ripping CD's, a bunch of eBay auction descriptions that I need to use and pictures of my cousin's wedding reception. :shock: Any suggestions?

---

### Post by trash on 2006-10-07
sad to say but there was nothing i could do with mine at all, it was my main root partition that lost it's format during an upgrade or when I installed on another partition... i searched the forums and tried fdisk and something else as per other threads but nothing helped.... painful I know.

---

### Post by GStubbs43 on 2006-10-07
err... I have no idea how it happened.... I never touched it and I was just using it today!

---

### Post by GStubbs43 on 2006-10-08
okay, I'm gonna bump this *one* more time :D sorry, but I really don't want to have to format that, which for some reason I think I'm gonna have to. ;) :(

---

### Post by Ocxic on 2006-10-08
try test disk, it's a partition, partition table recovery program.
it's in synaptic.

---

