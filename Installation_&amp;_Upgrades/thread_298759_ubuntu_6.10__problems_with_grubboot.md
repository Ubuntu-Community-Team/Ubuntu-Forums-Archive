---
title: "ubuntu 6.10 : problems with grub/boot"
date: 2006-11-13
forum: Installation &amp; Upgrades
---

### Post by gruadp on 2006-11-13
After Installing Ubuntu 6.10 my System did not boot - the bios couldnt find any bootloader.
I needed to boot from the Ubuntu-CD and then select "boot from first harddisk" to get to the grub-menu on my harddisk which works fine.

How can I install the missing first part of the boot-chain?

I tried  grub-install /dev/hda but this didnt change anything (menu.lst below).  
The ubuntu-help states that there should be a system->administration->disk application on my machine but there is not. I didnt find any GUI for grub or booting.

any help appretiated,
thnx
peter

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.


default         0
timeout         10

title           Ubuntu, kernel 2.6.17-10-generic
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.17-10-generic root=/dev/hda2 ro quiet splash
initrd          /boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title           Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.17-10-generic root=/dev/hda2 ro single
initrd          /boot/initrd.img-2.6.17-10-generic
boot

title           Ubuntu, memtest86+
root            (hd0,1)
kernel          /boot/memtest86+.bin
quiet
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title           Microsoft Windows XP Professional
root            (hd0,0)
savedefault
makeactive
chainloader     +1

---

### Post by pdub on 2006-11-13
I have fixed this in the past as follows.

1. Boot from the live CD

2. Open a terminal and type:

```
sudo grub
```

3. In grub type the following:

```
root (hd0,1)

setup (hd0)

quit
```

4. Reboot

---

