---
title: "Raid for Swap, using fstab"
date: 2007-04-29
forum: Installation &amp; Upgrades
---

### Post by damvcoool on 2007-04-29
ok i know there is a way to make a raid only for swap partitions  using the fstab but i dont remember how it works.

i remmember that there is a pri=1 or something like that can anyone help me

---

### Post by davidkahn on 2007-11-13
It's rather late to reply.  However, the answer is to add entries such as:[INDENT] /dev/sda2       swap           swap    defaults,pri=1   0 0
/dev/sdb2       swap           swap    defaults,pri=1   0 0
/dev/sdc2       swap           swap    defaults,pri=1   0 0
[/INDENT]all with the same priority, to /etc/fstab, and the kernel automatically stripes your swap space.

Good luck,

David

---

