---
title: "Please ExPLAIN!!!"
date: 2006-12-11
forum: Installation &amp; Upgrades
---

### Post by Mueez on 2006-12-11
hy guys...
i am facing start up problems with my ubunto...

please what could this mean???

[B]"
VHS:cannot open root device "<NULL>" or
please append a correct "root=" boot option unknown block(8,3)
Kernal panic not syncing:VFS:unable to mount root fs on unknown-block(8,3)
"[/B]

This came out when i made an attempt by using the special boot option.....

LIVE cd does not work either nor does it give me any error...BUT installation stucks when I click proceed After choosing language....

---

### Post by taurus on 2006-12-11
You need to specify where root partition, /, is.  It should look something like "root=/dev/hda1" if you installed it on the first partition of the first harddrive...

---

### Post by Mueez on 2006-12-11
Thanx for such a quick response...

i am new to lunix and ubunto...

Please guide step by step how to install ubunto on 3rd partition...

---

