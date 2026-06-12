---
title: "Regenerate fstab"
date: 2006-07-13
forum: Installation &amp; Upgrades
---

### Post by Paerez on 2006-07-13
Hey all-

I noticed that ubuntu does a great job detecting drives and such when I install it, but if I change the configuration of my drives, is there a way to have ubuntu automatically rescan my partitions and re-create fstab?

A lot of beginner users will probably not be able to edit their own fstabs when they change their disks, whats the solution?

---

### Post by Siegfried on 2007-04-09
This is a good idea, a tool to automatically update fstab entries for new partitions, drives, etc.

---

### Post by ffi on 2007-04-09
googling for the possibility to regenerate fstab I found this topic, so I guess it's not possible?

---

### Post by alkat on 2007-11-30
Anybody knows of a way to do this? I've just rebuilt the partition table of my HD (wiped off Windows in favour of Mandriva 2008) and I would like to regenerate the fstab file.

---

### Post by ruibernardo on 2007-11-30
Boot from a LiveCD. Ubuntu Desktop CD will do.

Click on the menu "Places" > "Computer" and then click on each partitions you use to mount them (including the swap partition).

When they are mounted, open a terminal (Applications > Acessories > Terminal) and type:
```
blkid
```Blkid outputs the UUIDs of the mounted partitions.

Then type:
```
gksudo gedit
```Open the fstab file you want to update (the one on the disk) and change the UUIDs so they match the output of the blkid command.

Save the file and reboot.

---

