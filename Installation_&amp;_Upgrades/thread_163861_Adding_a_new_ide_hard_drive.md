---
title: "Adding a new ide hard drive"
date: 2006-04-21
forum: Installation &amp; Upgrades
---

### Post by maxwas on 2006-04-21
hi all,

i found an old (working) ide hard disk, so i decided to add it to my ubuntu box as /media/spare

here is what i did: partitioned (hdd), formatted as ext3, added the /spare dir to /media, created the appropriate entry in fstab:
> /dev/hdd            /media/spare               ext3           defaults        1 2
when i done the above and rebooted, the system hangs. When i go in as recovery and comment the line out in fstab the system boots ok.

is there anything i am doing wrong/ i should be doing?

Any help would be greatly appreciated

thx in advance

max

---

### Post by Sutekh on 2006-04-23
The fstab entry needs to have a partition number,  /dev/hdd isn't enough.  If you formatted the hard disc without doing anything fancy to the partitions, I would guess it would be /dev/hdd1.  

Try changing the line to
```
/dev/hdd1   /media/spare   ext3   defaults   1   2
```

You can confirm this location with this command to list your partitions```
sudo fdisk -l
```

---

### Post by maxwas on 2006-04-23
Ah, of course :)

Thats it fixed, thanks.

---

### Post by Sutekh on 2006-04-23
Not a problem at all! :D

---

