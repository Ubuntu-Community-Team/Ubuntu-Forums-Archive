---
title: "grub error 17  on raid5"
date: 2006-10-30
forum: Installation &amp; Upgrades
---

### Post by jaa6c6 on 2006-10-30
I have 4 drives. The partition layout of each drive is

80 MB RAID 1         = 80 MB  ext2     /boot
15 GB RAID 5         = 45 GB  reiserFS /
384 MB SWAP          = 1.5 GB          SWAP
64 GB RAID 5 /home   = 192 GB reiserFS /home

So anyway the system boots but grub just gives me an error 17.

I looked at the menu.lst file in grub and it seems right (as far as I know)

The relevant bit(atleast i think its relevant) goes like this

title        Ubuntu etc..
root         (hd0,0)
kernel       /vmlinuz-2.6.17-10-generic root=/dev/md1 ro quiet splash
initrd       /initrd.img-2.6.17-10-generic
quit
savedefault
boot

So anyone know whats going on here? Why grub might not work in this situation?

---

### Post by Sef on 2006-10-31
GRUB 17 Error:

> 17 : Cannot mount selected partition
    This error is returned if the partition requested exists, but the filesystem type cannot be recognized by GRUB.

---

### Post by Jindro on 2006-10-31
The kernel file was not found.
have you got  /vmlinuz as link or as you specified vmlinuz-2.6.17-10-generic?

---

