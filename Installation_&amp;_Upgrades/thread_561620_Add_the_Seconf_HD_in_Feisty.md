---
title: "Add the Seconf HD in Feisty"
date: 2007-09-27
forum: Installation &amp; Upgrades
---

### Post by weiqiang on 2007-09-27
I've been having the feisty running for almost half a year now. I have one 160g hard drive and the free space is getting smaller since I downloaded a lot. I am thinking of adding the second hard drive in(maybe the 320 gb one), but I don't know how to get it work in feisty. I plan to have the second to store some huge downloaded files. Help appreciated! :)

---

### Post by Pumalite on 2007-09-27
Just install it. Make sure BIOS settings are OK. Then use Gparted to make one large partition of the whole drive formatted ext3 and you are done.

---

### Post by weiqiang on 2007-09-27
Thanks. How to use this disk after partition? it'll be /home or some other? This question might be very naive....I just want to make sure everything before I do it. Thanks.

---

### Post by logos34 on 2007-09-27
You need to add an fstab entry and create the mount point:
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

