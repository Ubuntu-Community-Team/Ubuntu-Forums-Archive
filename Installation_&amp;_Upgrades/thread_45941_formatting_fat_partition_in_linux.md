---
title: "formatting fat partition in linux"
date: 2005-07-02
forum: Installation &amp; Upgrades
---

### Post by dworzec.net on 2005-07-02
hi,
I have a windows fat32 partition which I want to format. However I can't do it in windows, as the system is broken. That is why I want to format this partition (plus repair broken blocks) from Ubuntu level. How to do that?
thanks in advance...

---

### Post by sonny on 2005-07-02
install qtparted: sudo apt-get install qtparted

---

### Post by sapo on 2005-07-02
[QUOTE=dworzec.net]hi,
I have a windows fat32 partition which I want to format. However I can't do it in windows, as the system is broken. That is why I want to format this partition (plus repair broken blocks) from Ubuntu level. How to do that?
thanks in advance...[/QUOTE]


easy ;)

you know what partition is right? if dont... type sudo fdisk -l to see its number...

then umount it.. and type:

mkfs.ext3 /dev/hda1 (or whatever is you partition)

thats it currently i m using reiserFS in my ubuntu  :grin: mkreiserfs works too

---

### Post by dworzec.net on 2005-07-02
thanks a lot, it was pretty easy with qtparted :)

---

