---
title: "Server upgrade to feisty -&gt; disks gone mad"
date: 2007-04-25
forum: Installation &amp; Upgrades
---

### Post by GoBieN on 2007-04-25
My situation.

My server started out as a dapper server, i had only few disks then. AFter upgrade to edgy the /etc/fstab was auto modified to the UUID system. Wich i don't understand one bit about.

After some time i added extra disks. I have no raid (its a home server) and no LVM's. As i said the UUID's are japanese to me so i added, manual entries in /etc/fstab. just old style -> /dev/hdb1 /mnt/disk ... you get the picture right. This wan't a problem for edgy. He mounted the partition good.

Now i upgrade to feisty and every disk i addes manually refused to mount. After nosing around it seems all the disks have changed from /dev/hd(abcd) to /dev/mapper/sdb(abcd)
Btw: These are all simple IDE disks (no sata) and i have 1 SCSI disk (formerly /dev/sda).

Why this changed i don't know, but i do suspect mdadm package. It asked me sometinh during upgrade wich i didn't know what to anwser to so i choose the default (ENTER).

I changed my fstab manually to /dev/mapper/sdb1 etc ... bu i don't know where my SCSI disk has gone to ?
And 1 partition refuses to mount because fschk says it can't find the superblock. But it was fine before ?

Can i convert back to the old situation by removing mdadm or so ? Please advise me.

---

### Post by GoBieN on 2007-04-25
pff i finally found all my disks.

hda -> sda
hdb -> sdb
hdc (cdrom)
hdd -> sdc
sda -> sdd

You can see were i was a little confused, with hdd becoming sdc and sda becoming sdd.
If have now entered UUID's in my fstab. I looked them up with dev-by-uuid thing and typed it over in fstab.

---

