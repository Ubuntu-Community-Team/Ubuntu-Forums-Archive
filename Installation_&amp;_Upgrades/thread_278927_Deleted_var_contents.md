---
title: "Deleted /var contents"
date: 2006-10-17
forum: Installation &amp; Upgrades
---

### Post by formyfriend on 2006-10-17
Hello,

My friend accidently removed all the files in the **/var** folder. Now he is not able to boot. He tried debconf-recofigure, which is also failing showing the error message: 

" debconf: DbDriver "config" couldnt open /var/cache/debconf/config.dat ".

During the booting GDM is also failing since the gdm looks in to the /var/lib/gdm .

Can any one of you help him.

---

### Post by Kateikyoushi on 2006-10-17
It is difficult to restore those files without backup. Those files are depend on your system and installation so can say unique.

You could try to recover those files as I assume you did not write much to the disk after it happened but most likely a reinstall is an easier and faster solution.

---

