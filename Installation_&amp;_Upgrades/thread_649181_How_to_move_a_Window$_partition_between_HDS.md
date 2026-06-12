---
title: "How to move a Window$ partition between HDS"
date: 2007-12-24
forum: Installation &amp; Upgrades
---

### Post by jorgepeixoto on 2007-12-24
Hi. I have two HDs: hda and hdb. hda is very slow, and hdb is even slower. hda currently has a M$ Window$ install. I want to move it to hdb, without data loss, so I can install Ubuntu in hda. How can I do that?

---

### Post by Pumalite on 2007-12-24
TrueImage
You can save the image to an external hard drive and restore back to the other drive.

---

### Post by jorgepeixoto on 2007-12-24
I don't have an external drive.

If I simply copy the files, will Windows boot? I know it works with linux (with LInux, I take care to preserve metadata such as permissions). I'll try it.

---

### Post by Pumalite on 2007-12-24
That's the way I used to do it light years ago, There are people in the forum that know more about these matters than I. Someone will chime in. Good luck!

---

### Post by jorgepeixoto on 2007-12-29
I kept Window$ in hda. I just used gparted to move the windows partition to the right, and shrink it. Then I could create a 384 MiB swap partition in the left, and a 8.7GiB reiserfs partition for Ubuntu just after the swap. Windows still works.

Problem solved.

---

### Post by Pumalite on 2007-12-29
Good for you!

---

