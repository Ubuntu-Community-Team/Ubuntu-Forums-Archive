---
title: "can I??"
date: 2006-06-11
forum: Installation &amp; Upgrades
---

### Post by KarmaKing on 2006-06-11
Hello all,

I want to install 6.06.  I am currently using Breezy dual boot with WIndows.  My questions are:

1. can I simply install over the current ubuntu?
2.  If I install over the current Ubuntu will I have still have the old kernel on my machine and will I be able to boot with it if anything goes wrong? (HD space is very small)
3.  if I choos to just uprgrade can I do it from the 6,06 CD?

thanks in advance

---

### Post by manicka on 2006-06-11
If hard disk space is limited I'd suggest a clean install in your / directory/partition but don't reformat your /home partition. That is assuming you have separate partition for /home.

---

### Post by KarmaKing on 2006-06-11
[QUOTE=manicka]If hard disk space is limited I'd suggest a clean install in your / directory/partition but don't reformat your /home partition. That is assuming you have separate partition for /home.[/QUOTE]
hello manika,

when you say /home partition are you refering to the current linux ext3 partition?

---

### Post by manicka on 2006-06-11
I mean how many partitions did you set up when you first installed Ubuntu? Do you have separate partions for / and /home or everything in one large partition?

---

### Post by KarmaKing on 2006-06-11
[QUOTE=manicka]I mean how many partitions did you set up when you first installed Ubuntu? Do you have separate partions for / and /home or everything in one large partition?[/QUOTE]
oh.

3 partitions.

one for windows.

one for FAT32, for windows and Ubuntu to share

one for Ubuntu

---

### Post by manicka on 2006-06-11
In that case you could try a dist-upgrade but people have been having mixed results. Try these links for info on how to do it.

[https://wiki.ubuntu.com/DapperUpgrades](https://wiki.ubuntu.com/DapperUpgrades)
[http://www.ubuntuforums.org/showthread.php?t=185467](http://www.ubuntuforums.org/showthread.php?t=185467)

Your cleanest option is a fresh install. Just backup your home directory and go for it. I'd also suggest making sperate partitions for you /, swap  and your /home directories when doing the clean install. This will make upgrades easier in the future.

Whichever way you go remember to backup your valuable data first

---

### Post by KarmaKing on 2006-06-12
thanks

---

### Post by nocturn on 2006-06-12
Before dist-upgrading, take a backup of /home (to a CD or to the FAT partition).

When copying to fat, use tar (archiver) to keep the permissions (which would be lost on FAT).

cd /home
sudo tar -czf /pathtofat/home.tar.gz *

would do it.  You can restore later:

cd /home
sudo tar -xzf /pathtofat/home.tar.gz

---

