---
title: "Ack. Messed up my XP's grub entry after a re-install."
date: 2008-03-23
forum: Installation &amp; Upgrades
---

### Post by tkawa6 on 2008-03-23
Hey all.
I'm having a problem booting into XP after re-installing it then re-installing grub. When I select windows I'm getting an *error 12.* It all was fine until te re-installs, but I did a stupid thing we installing XP by deleting its partition then re-creating it. XP is on the sda6 partition and I can view the files while in Kubuntu.

**fdisk -l**
> Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x86422a4f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2484    19952698+  83  Linux
/dev/sda2            2485        4522    16370235    f  W95 Ext'd (LBA)
/dev/sda3            4523       14593    80895307+   7  HPFS/NTFS
/dev/sda5            2486        2607      979933+  82  Linux swap / Solaris
/dev/sda6            2608        4522    15382206    7  HPFS/NTFS

**menu.lst**
> hiddenmenu
default 0
timeout 10

title Ubuntu hardy (development branch), kernel 2.6.24-12-generic
root (hd0,0)
kernel /boot/vmlinuz-2.6.24-12-generic root=UUID=557e9b6f-62c0-4b2d-9c7b-83626978b755 ro quiet splash
initrd /boot/initrd.img-2.6.24-12-generic

title Ubuntu hardy (development branch), kernel 2.6.24-12-generic (recovery mode)
root (hd0,0)
kernel /boot/vmlinuz-2.6.24-12-generic root=UUID=557e9b6f-62c0-4b2d-9c7b-83626978b755 ro single
initrd /boot/initrd.img-2.6.24-12-generic

title Ubuntu hardy (development branch), kernel 2.6.22-14-generic
root (hd0,0)
kernel /boot/vmlinuz-2.6.22-14-generic root=UUID=557e9b6f-62c0-4b2d-9c7b-83626978b755 ro quiet splash

title Ubuntu hardy (development branch), kernel 2.6.22-14-generic (recovery mode)
root (hd0,0)
kernel /boot/vmlinuz-2.6.22-14-generic root=UUID=557e9b6f-62c0-4b2d-9c7b-83626978b755 ro single

title Ubuntu hardy (development branch), memtest86+
root (hd0,0)
kernel /boot/memtest86+.bin

title Microsoft Windows XP
root (hd0,5)
chainloader +1
savedefault
makeactive


---

### Post by dstew on 2008-03-23
It looks correct. One guess is to change the order of the statements:```
title Microsoft Windows XP
root (hd0,5)
makeactive
savedefault
chainloader +1

```

---

### Post by geezerone on 2008-03-23
Found [**this**]("http://ubuntuforums.org/archive/index.php/t-464695.html") which may shed light too.

---

