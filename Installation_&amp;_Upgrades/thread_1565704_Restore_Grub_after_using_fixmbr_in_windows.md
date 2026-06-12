---
title: "Restore Grub after using fixmbr in windows"
date: 2010-09-01
forum: Installation &amp; Upgrades
---

### Post by -VJ- on 2010-09-01
I need to use the fixmbr command to fix my windows installation. I'd like to restore grub to its former state after doing so. I have searched how to do this and since my configuration differs slightly, I'd rather get more specific instructions. Right now this is what menu.lst looks like:

```

title		Ubuntu 8.04.1, kernel 2.6.24-21-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=0c5d1c9c-70bb-4f61-a0ad-7dc5e59d9713 ro quiet splash
initrd		/boot/initrd.img-2.6.24-21-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-21-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=0c5d1c9c-70bb-4f61-a0ad-7dc5e59d9713 ro single
initrd		/boot/initrd.img-2.6.24-21-generic

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=0c5d1c9c-70bb-4f61-a0ad-7dc5e59d9713 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=0c5d1c9c-70bb-4f61-a0ad-7dc5e59d9713 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,2)
kernel		/boot/memtest86+.bin
quiet

title		Other operating systems:
root

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows NT/2000/XP (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1

```

And fstab:

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=0c5d1c9c-70bb-4f61-a0ad-7dc5e59d9713 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda4
UUID=125b866a-6d3e-403e-bb6f-01ef05a8f772 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0


```

Also, I'm not sure if this is relevant, but when my system boots, grub stage 1.5 loads. After booting with an ubuntu 9.04 server disc, what menu options and commands do I need to enter to restore grub?

Thanks

---

### Post by andrewthomas on 2010-09-01
[https://help.ubuntu.com/community/GrubHowto#Backup,%20Repairing%20and%20Reinstalling%20GRUB](https://help.ubuntu.com/community/GrubHowto#Backup,%20Repairing%20and%20Reinstalling%20GRUB)

---

### Post by -VJ- on 2010-09-01
Thanks for your assistance. How do I access terminal after booting with a ubuntu 9.04 server disc?

---

### Post by andrewthomas on 2010-09-01
I don't know about the server disc, but you could try CTL+ALT+F2

---

