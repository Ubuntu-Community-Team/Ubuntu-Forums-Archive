---
title: "Boot with usb containing syslinux"
date: 2010-01-22
forum: Installation &amp; Upgrades
---

### Post by amsterdamharu on 2010-01-22
I don't have a cd player in my laptop so live cd is not an option. All I have here is a usb stick that has syslinux, I thought it could boot ubuntu located on my harddrive from syslinux on the usb stick but don't know how.

My system doesn't boot anymore, I can boot a usb stick containing TRK but that doesn't do much. I want to boot the ubuntu kernel and initrd that are on the harddrive so I can recover (kernel .... innitrd ... single). Both the kernel and initrd are on /dev/sda8/boot but can't tell syslinux to boot them.

Copied the kernel and initrd from sda8 to the usb then edited the syslinux.conf to add the following item:
label 4
menu label ^4 : boot ubuntu recover
kernel vmlinuz
append initrd=initrd ro root=/dev/sda8 single

Now working from my ubuntu and trying to install grub again.

---

### Post by C.S.Cameron on 2010-01-22
Is this solved?
Did you get your HD's grub fixed?

---

### Post by amsterdamharu on 2010-01-22
Yes, it's resolved.

Copied the kernel and initrd from sda8 to the usb with tynicore linux then edited the syslinux.conf to add the following item to the menu:

label 4
menu label ^4 : boot ubuntu recover
kernel vmlinuz
append initrd=initrd ro root=/dev/sda8 single

After the recover (no grub repair in recover) I have the option continue normal boot logged in and typed the following commands in a terminal:

```

sudo grub
find /boot/grub/menu.lst #for newer grub this should be find /boot/grub/grub.conf

```gives me (hd0,7)
```

root (hd0,7)
setup (hd0)
quit

```If grub doesn't find your drive you can issue the following commands before sudo grub:

```

sudo mkdir /mnt/root
sudo mount -t ext3 /dev/sda7 /mnt/root #sda8 has your /boot/grub dir
sudo mount -o bind /dev /mnt/root/dev
sudo chroot /mnt/root /bin/bash

```There is a more detailed howto here:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

