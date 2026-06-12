---
title: "Gets to boot then stalls. Help?"
date: 2006-07-22
forum: Installation &amp; Upgrades
---

### Post by microchip13 on 2006-07-22
I had another thread in the desktop forum, however upon closer inspection I figured this place would be more suitable. Mods if this is against the rules, feel free to delete the threads and I apologize.

I'm trying to install Ubuntu on a Pentium 4 with about a gig of RAM I believe on a 250GB Maxtor Drive.

The Install process was successful, however I cannot boot into Ubuntu.
When I try to boot it:

Booting 'Ubuntu,kernel 2.6.15-23-386'

root (hd0,0)
Filesystem type is ext2fs, partition type 0x83
kernel /boot/vmlinux-2.6.15-23-386 root=/dev/hda1 ro quiet splash
[Linux-bzImage. setup =0x1c00, size = 0x15774d]
initrd /boot/initrd.img-2.6.15-23-386
[Linux-initrd @ 0x1f942000, 0x6ad37b bytes]
savedefault
boot


And it just hangs here. I really need to get this working.

I've gone through with some GRUB commands that are pretty much the same, but using root=/dev/hda(Something close to that anyway.) and I can get it to uncompress the kernel and start booting, then it kernel panics.

As said, I'd really like to get this working. Any advice?

TiA.

---

### Post by taurus on 2006-07-22
Looks like you don't have a seperate /boot and you've installed everything on /--/dev/hda1!  Is that right?

---

### Post by Ocxic on 2006-07-22
When it says to press esc to go into the grub menu, press e on the your new kernel should be the only one there. and edit ti to look like this:

root (hd0,0)
Filesystem type is ext2fs, partition type 0x83
kernel /boot/vmlinux-2.6.15-23-386 root=/dev/hda1 ro quiet splash
initrd /boot/initrd.img-2.6.15-23-386
savedefault
boot

---

### Post by microchip13 on 2006-07-22
I did whatever the default layout creates.


This is just the boot after finishing the install from the Live CD.

---

