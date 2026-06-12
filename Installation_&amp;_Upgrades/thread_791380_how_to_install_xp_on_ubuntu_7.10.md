---
title: "how to install xp on ubuntu 7.10"
date: 2008-05-12
forum: Installation &amp; Upgrades
---

### Post by n_123sum on 2008-05-12
i have dual boot os's that were working well
i have ubuntu 7.10 what happened was my xp os gave me some problems i had to reinstall it

without much knowledge i simply installed xp
i could not see any grub loader and simply xp was booting

i have installed grub loader but ubuntu os is booting well and i'm using it unfortunatly xp is not booting and giving error

xp partition is also not mounting in ubuntu os giving an error as


Unexpected clusters per mft record (-1). failed to mount '/dev/sda1': invalid argument the device  '/dev/sda1' doesn't have a valid NTFS. Maybe you selected the wrong device? or the whole disk instead of a partition ( e.g  /dev/hda, not  /dev/hda) ? the other way around?

please help me out

---

### Post by forestpixie on 2008-05-12
Can you open a terminal, run these commands and post the outputs please

```
ls /boot/grub/menu.*
cat /boot/grub.menu.lst
```

Edit this one also

sudo fdisk -l

---

### Post by housam on 2008-05-12
please type [COLOR="Red"]sudo fdisk -l[/COLOR] in a terminal and post the results where -l is a small L.

---

