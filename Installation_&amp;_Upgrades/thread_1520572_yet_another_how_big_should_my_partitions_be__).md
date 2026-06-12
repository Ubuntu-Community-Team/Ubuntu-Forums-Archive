---
title: "yet another how big should my partitions be  :)"
date: 2010-06-29
forum: Installation &amp; Upgrades
---

### Post by Ojustaboo on 2010-06-29
Hi all

750GB drive just for linux.

The size of the root is where I'm getting a little confused.

I like various MMORPG games and will want things like Lord of the Rings Online installed and possibly a few others.

If I install these through the likes of wine, do they go somewhere in the root partition tree, or the separate home partition?

Lord of the rings is 13GB under win7.

Want as much space for home as possible but also want to make sure I give the root partition enough space.

Also I've read about the benefits of having a /data partition for main storage.  In that scenario, do I leave /home as part of the root tree and simply create a separate /data partition for my videos etc?

What's the recommended file-system nowadays?  ext3, ext4 etc?  

many thanks

(64 bit system, 6GB RAM, 10.04 LTS)

---

### Post by darkod on 2010-06-29
If the disk is only for linux I highly recommend LVM. You can resize partitions in LVM without need to format, even while the system is running.
No need to break your head calculating right now. Just allocate some approx sizes, and you can always change later.
To get you going with LVM:
[http://linuxbsdos.com/2008/11/11/lvm-configuration-in-ubuntu-810/all/1/](http://linuxbsdos.com/2008/11/11/lvm-configuration-in-ubuntu-810/all/1/)

Few points:
- you need to use the alternate install cd
- you need to create primary /boot partition outside the LVM so it can boot

I'm sure you won't be disappointed.

---

### Post by Ojustaboo on 2010-06-29
Thanks, downloading now :)

---

### Post by darkod on 2010-06-29
I'm not sure it's mentioned in that article, but these days of course there are also graphical tools to control your LVM after install. And the LVM today is second generation LVM2.

Depending whether you are more familiar with command line or graphical interface, just search for graphical tools for LVM2 for ubuntu. Even the Software Center has some if you type LVM or logical volume manager in the search box.

---

### Post by Ojustaboo on 2010-06-29
Excellent, thanks for your help

---

