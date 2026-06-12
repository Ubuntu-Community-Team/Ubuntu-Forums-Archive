---
title: "Coping system on another disk, still boots to old one"
date: 2011-10-16
forum: Installation &amp; Upgrades
---

### Post by hackys on 2011-10-16
Hi. Every time I'll do upgrade to newer version of Ubuntu, i'll copy my system partition on another disk and there i try to do the upgrade process. If it's working like it should i'll do it on the original partition. But now i've got some problem doing that.
I've copied the system using live usb:
```
sudo cp -a /media/system/* /media/linux-backup
```
I've edited a line in /media/linux-backup/etc/fstab > uuid of partition mounted as "/" to the uuid of the linux-backup partition.
Then i've booted to the original 11.04 made:
```
sudo update-grub
```
with the result of:
```
Generating grub.cfg ...
using custom appearance settings
Found background image: grub_background.jpg
Found linux image: /boot/vmlinuz-2.6.38-11-generic
Found initrd image: /boot/initrd.img-2.6.38-11-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Ubuntu 11.04 (11.04) on /dev/sdc1
Found Windows 7 (loader) on /dev/sdd1
done
```

But if I choose the Ubuntu 11.04 on sdc (this is the linux-backup partition) it will boot me in the original one. Why's that?

EDIT: Adding the /boot/grub/grub.cfg after update-grub: [http://pastebin.com/hCb9XibT](http://pastebin.com/hCb9XibT)

---

