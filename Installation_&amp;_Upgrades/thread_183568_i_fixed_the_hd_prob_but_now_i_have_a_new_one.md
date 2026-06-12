---
title: "i fixed the hd prob but now i have a new one"
date: 2006-05-28
forum: Installation &amp; Upgrades
---

### Post by Iron_550 on 2006-05-28
ok i fianaly got my hd prob fixed after 6-8 hours of working on it but now in the mittle of ubuntu comming on theres this:
*checking all files....
fsck.ext3: NO such file or directory while trying to open /dev/hda1/dev/hda1:


the superblock could not be read or does not describe a corect ext2 filesystem. If the device is valid and it really contains an ext2 filesystem (and notswap or ufs or somthingelse), then superblock is corrupt, and you might try running e2fsck with an alternate superblock: e2fsck: -d 8198<device>


fsck failed plz repair manually.


any help?? thx

only had 3 houres of sleep


dev/mapper/ubuntu-root / ext3 defaults, errors=remount-ro0
1
/dev/hda1 /boot ext3 defaults 0 2
dev/mapper/ubuntu-swap_1 none swap sw 0 0
/dev/hdd media/crom0 udf , iso960user , noauto 0 0
/dev/fd0 /media/floppy0 auto rw, user, noato 0 0

---

### Post by adwait on 2006-05-28
Coud you post the output of:
```
sudo fdisk-l
```

Maybe you are trying to mount a extended partition instead of an actual one...

---

### Post by blackweaver on 2006-05-29
do you have only 1 linux installation? if you have 2 or if you have a live cd you could try doing fsck from the other

---

### Post by Iron_550 on 2006-05-29
i am fixed do worryes

---

### Post by Iron_550 on 2006-05-29
i am fixed no* worryes

---

