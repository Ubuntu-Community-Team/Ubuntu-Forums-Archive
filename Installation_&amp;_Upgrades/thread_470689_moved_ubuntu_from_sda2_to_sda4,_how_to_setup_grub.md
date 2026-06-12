---
title: "moved ubuntu from /sda2 to /sda4, how to setup grub?"
date: 2007-06-11
forum: Installation &amp; Upgrades
---

### Post by ulli.winter on 2007-06-11
hi,
i want to enlagrge my ubuntu partition, but i only have free space in front of the partition - therefore i copied the ubuntu partition (sda2 the old one, sda4 the copy) and want to boot the sda4.
i tried to change menu.lst, but simply changing root(hd0,1) to (0,3) didnt do it. (it booted from sda2 anyway)
do i have to change the "uuid=" line?
if... how?
"
title		Ubuntu, kernel 2.6.20-16-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=ccc9aea2-1344-4db2-ac83-02ddc129e7f2 ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic"

THANKS!

---

### Post by volksman on 2007-06-11
You will need to change the UUID value.  However I'm not sure how to find out what UUID is for each partition.   You will also need to update your /etc/fstab file to indicate the new mount points.

Hopefully someone will post how to find out what the proper UUID value is on a particular system.  I've been meaning to find out for a while now.. :)

---

### Post by ulli.winter on 2007-06-11
blkid
seems to show all uuids
...trying my luck

brb (hopefully *G*)

ps... sda2 and sda4 have the same uuids(??)

---

### Post by cyberdork33 on 2007-06-11
just use the block definitions and forget UUID. Replace them with /dev/sdaX (where is X is the appropriate partition number). Same can be done in fstab.

---

### Post by ulli.winter on 2007-06-11
ok... no fun at all - but it finally works :D

substitutiung uuid with /dev/sda worked fine
though there were some other problems.... *G*

thanks for your help!

---

