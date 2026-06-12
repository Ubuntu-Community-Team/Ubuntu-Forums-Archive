---
title: "aufs as root."
date: 2010-02-04
forum: Installation &amp; Upgrades
---

### Post by xanthax on 2010-02-04
Hi, im trying to get aufs as root drive but cant find any GOOD informational links.
Just a lot of half way not so well explained scripts...

The thought is to get my /dev/sda2 which is my root to be mounted ro and a tmpfs as mounted over it so everything that is written to / is written the tmpfs.

I have never used aufs before but from what i can understand it's only to do like this.

# mount -t tmpfs tmpfs /rw
# mount -t ext3 -o ro /dev/sda2 /ro
# mount -t aufs -o dirs=/ro:/rw /

And then convert it into fstab structure and put it in fstab.


But still there has to be some kernel modules or alike and a lot of other requierments ?


I have Ubuntu 9.10 and have made a minimal (custom) install from a server install cd without adding or removing any extra packets.


Any help would be appreciated.

Regards
//XanthaX

---

