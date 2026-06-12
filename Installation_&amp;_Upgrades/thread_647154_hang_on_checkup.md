---
title: "hang on checkup"
date: 2007-12-22
forum: Installation &amp; Upgrades
---

### Post by twist2b on 2007-12-22
sorry but i cant load ubuntu anymore and im dieing.... it starts checking the partition every 30 times it seems... but on checkup it ALWAYS freezes... anyway to bypass this?

i thought i could go into recovery mode and not have to deal with it.... but thats not the case seeing that i have to checkup on recovery mode aswell aparently... once i can get in ill just do this..



[PHP]Sudo tune2fs –c 0 /dev/sd1  [/PHP]

any way to bypass though?

---

### Post by Thanoulis on 2007-12-22
Boot from a CD, or something, and edit your /etc/fstab file. The line where yout hd is mounted, ends with a 1. Change it to a 0. That will disable auto fsck.

---

