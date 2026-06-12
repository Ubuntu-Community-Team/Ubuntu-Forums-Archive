---
title: "how do i get rid of dual-boot"
date: 2008-11-02
forum: Installation &amp; Upgrades
---

### Post by duffy_ryan on 2008-11-02
So i have ubuntu and xp dual-booted on my desktop, but now I wanna get rid of the ubuntu part (keeping it on the laptop though). How do I go about doing this successfully? Thanks.

---

### Post by Partyboi2 on 2008-11-02
Boot a ubuntu live cd  and open up gparted (System>Admin>Partition Editor) and delete your ubuntu paritions (make sure you stay away from the ntfs partition(s) then after you have deleted them boot a  windows xp disk into recovery mode and type
```
fixmbr
``` If you don't have a windows disk then you could try using [[COLOR=Blue]super grub[/COLOR]]("http://www.supergrubdisk.org/") to fixmbr or see [[COLOR=Blue]this[/COLOR]]("http://www.users.bigpond.net.au/hermanzone/p18.htm") for more options

---

