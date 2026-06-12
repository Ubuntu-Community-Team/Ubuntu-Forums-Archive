---
title: "Cant mount Fat32 FileSystem"
date: 2005-07-18
forum: Installation &amp; Upgrades
---

### Post by john_van_v on 2005-07-18
Note***  forget everything I wrote, on my second attempt the mount worked



Hello all, I am using the LiveCD and this is so far been a beautiful experience.. but..

mount -t vfat /dev/hda3 /mnt/hda3

Told me that vfat is not supported so I searched the web and found:

modprobe nls_cp437
modprobe nls_iso8859-1
modprobe vfat

That produced slightly moreresults, but the modprobe vfat complained about lots of "lost symbols"

This request really comes from a user in my linux club:
[http://www.care2.com/c2c/group/lnxsoc](http://www.care2.com/c2c/group/lnxsoc)

---

### Post by ketiko on 2005-07-19
Try switching "-t vfat" after you list your directories.

sudo mount /dev/hda3 /mnt/hda3 -t vfat

See the [Unofficial Ubuntu Starter Guide](http://ubuntuguide.org/#mountunmountfat) .  I did this and it worked fine.  However, only root can access it this way.   For your user to access it do:

sudo mount /dev/hda3 /mnt/hada3 -t vfat -o user="then your user name"

This worked for me.  Hope it helps.

---

