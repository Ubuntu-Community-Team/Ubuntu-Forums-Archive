---
title: "Can't run Ubuntu"
date: 2012-11-24
forum: Installation &amp; Upgrades
---

### Post by eagleseye on 2012-11-24
I can not get 12.04 or 12.1 to run on this PC since replacing the MB and installing Win 7. In fact after replacing the MB and running XP , Ubuntu wouldn't run but did see my second HDD, in Win 7 it doesn't. I have a [SIZE=2] 775Dual-VSTA MB, 2.8 dual core Intell PCU, an [/SIZE]
[SIZE=2]ATI Radeon HD 5450 v[SIZE=2]ideo card, 2gigs of memory, high defin[SIZE=2]ition audio card. I also have a Brother printer connected. Maybe I should unplug it and try again. Thanks for your help.[/SIZE][/SIZE]
[/SIZE]

---

### Post by Bashing-om on 2012-11-25
eagleseye; Hi !

for starters, show what there is to work with/from:
in the liveCD environment; Boot up the liveCD in "try ubuntu" mode.
Post the output of terminal commands:
```
sudo fdisk -lu
sudo parted -l
sudo parted /dev/sda unit s print

```[INDENT]we will see what there is to be seen <== BDQ

[/INDENT]

---

