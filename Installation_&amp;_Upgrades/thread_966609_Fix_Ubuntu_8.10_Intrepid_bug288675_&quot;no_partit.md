---
title: "Fix Ubuntu 8.10 Intrepid bug/288675 &quot;no partitions listed in partition table&quot;"
date: 2008-11-01
forum: Installation &amp; Upgrades
---

### Post by gulch on 2008-11-01
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/288675](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/288675)
no partitions listed in partition table

That is an easy way to solve the problem:
1. plesae use the Alternative iso;

2. when partition, run shell, you can see /hd-media,
only need run as following:
[COLOR="Red"][SIZE="7"]# umount -l /hd-media
# exit[/SIZE][/COLOR]

3. now you can see partition tab, good luck!!!:lolflag:

---

### Post by gibberz on 2008-11-02
Thanks Gulch mate , now i`m rocking in all the intrepid glory :lolflag:

---

