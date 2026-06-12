---
title: "Uninstall from live cd?"
date: 2008-06-20
forum: Installation &amp; Upgrades
---

### Post by KingTuby on 2008-06-20
Is it possible to uninstall from the livecd? I have installed ubunto and made a pigs ear of it - i get a grub 5 error and cant get into either linux or vista.

Is there a way of rolling back my pc so its back to vista only? I can then have another go at installing ubuntu

cheers

---

### Post by Pumalite on 2008-06-20
Use gparted (on the Live CD) and erase Ubuntu and it's partitions. Then fix your Windows MBR with Super Grub:
[http://users.bigpond.net.au/hermanzone/supergrubdiskpage.html](http://users.bigpond.net.au/hermanzone/supergrubdiskpage.html)
Burn to disk and boot from it.

---

### Post by KingTuby on 2008-06-20
Im must be being dim - where is the gparted app on the disc - i cant see it???

---

### Post by timcredible on 2008-06-20
System -> Administration -> Partition Editor.

If you're not planning on trying linux again, you can add that extra drive space back to your ntfs partition.

And super grub disk is great, but not the easiest to follow, read the screens carefully, and you'll be able to restore the MBR so it looks like you  never had linux on your machine.

---

