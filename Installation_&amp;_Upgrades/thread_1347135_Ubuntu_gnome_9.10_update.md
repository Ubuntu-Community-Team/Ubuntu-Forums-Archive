---
title: "Ubuntu gnome 9.10 update"
date: 2009-12-05
forum: Installation &amp; Upgrades
---

### Post by kamelteo on 2009-12-05
GOOD OLD REINSTALL FIXED EVERYTHING ; BUT NOW :


[img]http://www.upload.ee/image/288669/DSC01111.JPG[/img] , how to get rid of last 6 lines of grub .... it also drained my HDD and im not interested formatting everything again >.<

---

### Post by some-what-Gnu-2-networks on 2009-12-05
Had same problem, reinstalled, problem disappeared. Always back-up your data.

---

### Post by kamelteo on 2009-12-06
okay thanks [some-what-Gnu-2-networks]("http://ubuntuforums.org/member.php?u=966853") , i reinstalled , but now im facing another problem ... i think i've installed ubuntu twice by accident ( 1 works , 2nd doesnt)

any idea guyse?

---

### Post by darkod on 2009-12-06
You can delete/format the partition(s) of the older nonworking install and then running update-grub will not detect it (because it's not there). But that space will remain unused unless you format it as ext4 or ntfs and use as data partition or similar.
I don't know in details your disk layout and partitions. If reinstalling ubuntu you need to select the manual partitioning option and tell it to use the existing partitions. Otherwise you end up like this, with 2 ubuntu installations.

---

