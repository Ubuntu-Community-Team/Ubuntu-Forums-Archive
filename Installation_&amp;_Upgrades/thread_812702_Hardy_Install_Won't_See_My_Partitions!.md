---
title: "Hardy Install Won't See My Partitions!"
date: 2008-05-30
forum: Installation &amp; Upgrades
---

### Post by bpont on 2008-05-30
I need to do a clean install of Hardy but the install disk will not see my partitions on /dev/sdb.  It just lists the 'entire disk' and therefore, I would need to create a new table and blow away all my data, which is not an option.

Curiously, under gnome, gparted sees my lvm partition which resides on /dev/sdb 
[http://i30.tinypic.com/2jb3aqr.jpg](http://i30.tinypic.com/2jb3aqr.jpg) 
but it will not see the partitions on /dev/sdb directly
[http://i26.tinypic.com/2eeific.png](http://i26.tinypic.com/2eeific.png) 
however, cfdisk sees all the partitions on /dev/sdb 
[http://i31.tinypic.com/xqm83p.png](http://i31.tinypic.com/xqm83p.png)

Obviously, I possess a valid partition table that is being used by Ubuntu and LVM2.

Why won't the Hardy install disk see my partitions and allow me to chose one of them to mount / and another for swap and my lvm for /home?

---

