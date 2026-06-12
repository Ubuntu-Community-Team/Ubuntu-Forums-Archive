---
title: "ext3 vs ntfs"
date: 2007-12-18
forum: Installation &amp; Upgrades
---

### Post by puner on 2007-12-18
hello,

i formated a 120gb drive into three partitions. Xp, Vista, and Ubuntu all NTFS.

When I go to use the Live CD ubuntu does not see all the partitions, instead it just says 120gb.

Also, what file system does the Ubuntu partition need to be formated in?

---

### Post by Partyboi2 on 2007-12-18
Use ext3 for ubuntu, it works best.

---

### Post by puner on 2007-12-19
And what program can do this on windows?

---

### Post by Partyboi2 on 2007-12-19
When you do the ubuntu install the installer is going to create a ext3 partition.
 Another way is to use gparted that is on the ubuntu live cd, it can be found under System>Admin>Partition Editor.
The first option is the easiest.
If you are planning on triple booting, this might come in use.
[http://apcmag.com/node/5162/](http://apcmag.com/node/5162/)

---

### Post by puner on 2007-12-19
Alright so I made the third partition into ext3 and ubuntu still wont install there.

[[IMG]http://imagenerd.com/thumbnails/th_screenshotpJ1M.png[/IMG]](http://imagenerd.com/show.php?_img=screenshotpJ1M.png)

---

### Post by Partyboi2 on 2007-12-20
you need to define where the /(root) partition will be,
right-click on the partition ext3 and click edit. From here change the mount point to a forward slash / and click OK.
 If you are manually going to partition you will also need to create a
/root (min 5 gig)
/swap (about 1gig)
/home
Here is a how-to on manually partition
[http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty](http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty)

---

