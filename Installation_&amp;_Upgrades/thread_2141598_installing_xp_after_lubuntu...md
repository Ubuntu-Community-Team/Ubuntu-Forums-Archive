---
title: "installing xp after lubuntu.."
date: 2013-05-03
forum: Installation &amp; Upgrades
---

### Post by robin. on 2013-05-03
i installed lubuntu with drive encryption several months ago..  this encompassed the whole hard drive.

i want to tag on a small install of windows xp for gaming

is this possible without having to back-up, and perform a bunch of reinstallations?

love,

robin :)

---

### Post by robin. on 2013-05-03
Aha... good ol' google: [http://askubuntu.com/questions/6317/how-can-i-install-windows-7-after-ive-installed-ubuntu](http://askubuntu.com/questions/6317/how-can-i-install-windows-7-after-ive-installed-ubuntu)

---

### Post by Lars Noodén on 2013-05-03
With drive encryption you won't be able to resize the partition.  You can try it to be sure, but if I recall correctly it does not work.  So unfortunately you'll have to backup and reinstall to leave something for XP.  Also Windows does not play nice with other systems, so you'll have to install it first or be prepared to repair things like Grub.

---

### Post by Mark Phelps on 2013-05-03
Note that if you TRY to shrink the encrypted partition, and it fails for any reasons, that is likely going to end up corrupting the ENTIRE partition!

The safest way to do this is the following:
1) decrypt the filesystem
2) shrink the filesystem using GParted from LiveCD or LiveUSB
3) Recrypt the shrunken partition

There are threads around that show how to do this differently if you encrypted using LUKS -- but this is the safest way to do it.

---

### Post by pfeiffep on 2013-05-03
Another option to consider is use Virtual Box

---

