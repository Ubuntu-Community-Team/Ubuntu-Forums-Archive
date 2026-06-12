---
title: "Multi Boot"
date: 2010-05-05
forum: Installation &amp; Upgrades
---

### Post by dontgetshocked on 2010-05-05
I have installed Ubuntu 10.04/Mandriva 2010/XP.

XP /dev/sda1
Mandriva /dev/sda4
Ubuntu /dev/sda5
Swap Space /dev/sda2
Free /dev/sda

I must have done something wrong since Mandriva does not show up in Ubuntu's boot menu.How can I fix this? I partitioned /dev/dev4 for Mandriva and I think I chose ubuntu as the boot!?!

---

### Post by nitstorm on 2010-05-05
ubuntuforums.orgubuntuforums.org/newreply.php
```

sudo fdisk -l

```

The partition with star should tell you where the bootloader is loading from.

and have you run
```

sudo update-grub

```
to see if the mandriva partiton is being detected?

---

### Post by dontgetshocked on 2010-05-05
Unable to seek on /dev/sda
david@Netbook:~$ 
this is the message i get

error: cannot seek `/dev/sda'.
error: cannot seek `/dev/sda'.
Generating grub.cfg ...
error: cannot seek `/dev/sda'.
error: cannot seek `/dev/sda'.
error: cannot seek `/dev/sda'.
error: cannot seek `/dev/sda'.
error: cannot seek `/dev/sda'.
error: cannot seek `/dev/sda'.
error: cannot seek `/dev/sda'.
error: cannot seek `/dev/sda'.
error: cannot seek `/dev/sda'.
Found linux image: /boot/vmlinuz-2.6.32-21-generic
Found initrd image: /boot/initrd.img-2.6.32-21-generic
error: cannot seek `/dev/sda'.
error: cannot seek `/dev/sda'.
error: cannot seek `/dev/sda'.
Found linux image: /boot/vmlinuz-2.6.31-21-generic
Found initrd image: /boot/initrd.img-2.6.31-21-generic
Found linux image: /boot/vmlinuz-2.6.31-20-generic
Found initrd image: /boot/initrd.img-2.6.31-20-generic
Found memtest86+ image: /boot/memtest86+.bin
error: cannot seek `/dev/sda'.
error: cannot seek `/dev/sda'.
error: cannot seek `/dev/sda'.
Found Microsoft Windows XP Home Edition on /dev/sda1
error: cannot seek `/dev/sda'.
error: cannot seek `/dev/sda'.
error: cannot seek `/dev/sda'.
Found Mandriva Linux 2010.0 (2010.0) on /dev/sda4
error: cannot seek `/dev/sda'.
error: cannot seek `/dev/sda'.
error: cannot seek `/dev/sda'.
done
david@Netbook:~$

---

