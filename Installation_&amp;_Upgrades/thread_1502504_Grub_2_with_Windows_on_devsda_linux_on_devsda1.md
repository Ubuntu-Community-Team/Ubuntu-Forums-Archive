---
title: "Grub 2 with Windows on /dev/sda linux on /dev/sda1"
date: 2010-06-05
forum: Installation &amp; Upgrades
---

### Post by frkstein on 2010-06-05
I tried to update my system from 9.10 to 10.04 but when the system boots it says that it can not find the symbol for grub_puts_ and drops me into grub rescue.

I have a live disc and have been trying to get grub to reinstall following the advice from different websites and forum threads. It seems that everything goes smooth until I get to the part where you run update-grub. At that point I get the following:

/usr/sbin/grub-probe: error: cannot find a device for / ( is /dev mounted?).

My configuration is as follows:
windows is loaded on /dev/sda1. fdisk -l lists this partition as bootable.
linux / is loaded on /dev/sdb1
/usr is loaded on /dev/sdb5
/var is loaded on /dev/sdb6
/home is loaded on /dev/sdb9

As I have said, I have run the following commands:
sudo fdisk -l

sudo mount /dev/sdb1 /mnt
sudo mount --bind /dev /mnt/dev
sudo mount --bind /proc /mnt/proc
sudo mount --bind /sys /mnt/sys

sudo -i *note I tried sudo chroot /mnt but it causes problems with bash

update-grub

this is where I have problems. it says:
/usr/sbin/grub-probe: error: cannot find a device for / ( is /dev mounted?).

any suggestions on how I can fix this grub problem?

---

### Post by darkod on 2010-06-05
You shouldn't need update-grub at that moment. Without the chroot command it will give you that error because without the chroot you are still in live mode.
The chroot /mnt allows it to "enter" your hdd install so that update-grub looks like executed from there.

Anyway, first make sure you are booting from the /dev/sdb disk, it needs to be first in hdd boot order. After that you can reinstall grub2 to /dev/sdb from live mode with:

sudo mount /dev/sdb1 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sdb

That's all you need. That should allow you to boot into ubuntu.

If you need to update the grub.cfg, once you boot into ubuntu do:

sudo update-grub

---

### Post by frkstein on 2010-06-05
darkod, thanks for your instructions. I changed the physical placement of my drives in the computer so that linux show as the /dev/sda drvie and windows /dev/sdb. Without doing anything else, grub worked perfectly on the next boot.

thanks again.

---

