---
title: "GParted and Swap"
date: 2007-02-27
forum: Installation &amp; Upgrades
---

### Post by j2satx on 2007-02-27
If I use GParted LiveCD to modify my Ubuntu 6.10 partitions, Ubuntu no longer recognizes the Swap space.

If I reinstall Ubuntu 6.10 using the modified partitions, Ubuntu will then recognize the Swap space.

Bummer to have to install twice.

How should I modify the partitions so I do not need a reinstall?

---

### Post by bulldog on 2007-02-27
Just reformat the swap as  swap and it should be recognized.
Never had this problem though.......but it should help.

---

### Post by j2satx on 2007-02-27
I reformatted the swap partition after the modification.

---

### Post by bulldog on 2007-02-27
Modifying your partitions without reinstalling is possible.
You have to keep something in mind though,resizing isn't a problem generally,but if you delete or create partitions,you have to modify your fstab and menu.lst for sure.

---

