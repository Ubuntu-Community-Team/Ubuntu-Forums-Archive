---
title: "Backup whole partition as image than format disk and put it back"
date: 2014-12-08
forum: Installation &amp; Upgrades
---

### Post by joska1201 on 2014-12-08
Hi I have Ubuntu on a half a disk, and want to do dual boot....... But Vista have some problems with this config I simply can not isntall tham (Can not restart the computer or smthg msg)

I sure that installling win first on clean hardisk will solve the problem. But my Ubuntu is fully customized I dont want to do fresh install.

So my plan basicly is (tell me if it is even possible)

1) bckup partiton with ubuntu as disk image
2) format disk install vista
3) now thats the tricky part wich I am not sure if it is even possible . Get ubuntu partition back to unlocated space on disk, reinstall grub and voila :-) - but thats the idea, can someone tell me if it is possible before I start?

thx

---

### Post by Mark Phelps on 2014-12-08
As to 1:, you don't want a "disk image"; instead, you want a "partition image".  If you restore from a disk image, it will erase the entire target disk and reformat it to match the formatting of the saved disk image.  If you restore from a partition image, it will only write that partition to the drive.

Two apps I've used to do partition images: Clonezilla and RedoBackup

As to 3: Sorry, only used these to restore partitions, not to migrate partitions.  SO, don't know if either would leave the Vista partition intact when you do the restore.

---

### Post by joska1201 on 2014-12-08
ok got it [https://wiki.debian.org/Backup/Clone](https://wiki.debian.org/Backup/Clone)

---

### Post by joska1201 on 2014-12-08
thx man for quick reply

---

