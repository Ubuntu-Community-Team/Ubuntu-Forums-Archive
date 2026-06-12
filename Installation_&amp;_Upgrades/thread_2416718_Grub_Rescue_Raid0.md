---
title: "Grub Rescue Raid0"
date: 2019-04-14
forum: Installation &amp; Upgrades
---

### Post by cagnulein2 on 2019-04-14
Hello everybody, i've got a strange behaviour on my ubuntu system with raid0.


I've installed it from the alternative install and everything works flawless unless I power it off.


When i power it off a grub rescue error appears ( error [https://photos.app.goo.gl/fLcQk7YZkfBk6Gwk6](https://photos.app.goo.gl/fLcQk7YZkfBk6Gwk6) )


**error: disk 'mduuid/14e73f9cc7c419f14668ccc2d3f69343' not found.**


The strange this is that if a boot from USB and I run a:
[I][B]grub-install /dev/sda
grub-install /dev/sdb
[/B][/I]

everything goes fine until the next poweroff.


I write "poweroff" because if I reboot everything went fine.


I guess it's a matter of uuid but i don't know how to solve it definitevely.


This is my /dev/disk/by-id


cagnulein@linux:~$ ls /dev/disk/by-id/ -ltr
total 0
lrwxrwxrwx 1 root root  9 apr 14 08:55 ata-ST3250620AS_9QE1RCKN -> ../../sdb
lrwxrwxrwx 1 root root  9 apr 14 08:55 ata-ST3250620AS_9QE3SFB3 -> ../../sda
lrwxrwxrwx 1 root root  9 apr 14 08:55 md-uuid-14e73f9c:c7c419f1:4668ccc2:d3f69343 -> ../../md0
lrwxrwxrwx 1 root root  9 apr 14 08:55 md-name-_none_:0 -> ../../md0
lrwxrwxrwx 1 root root 10 apr 14 08:55 ata-ST3250620AS_9QE1RCKN-part1 -> ../../sdb1
lrwxrwxrwx 1 root root 10 apr 14 08:55 ata-ST3250620AS_9QE3SFB3-part1 -> ../../sda1

---

