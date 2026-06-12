---
title: "Grub: Cannot mount partition"
date: 2007-04-28
forum: Installation &amp; Upgrades
---

### Post by jammeri on 2007-04-28
I tried to install Faisty Fawn from CD... Seemed to go just fine... booted my computer and selected to boot Ubuntu. Got error message saying Unable to mount partition.

I got Asus P5B Deluxe motherboard with onboard raid controller. (Dunno if it's active tho as I only have 1 hard drive)

I have 4 partitions: /dev/sda1 (NTFS), /dev/sda2 (NTFS), /dev/sda3 (EXT3, mounted as root) and /dev/sda4 (SWAP)

got following settings in my grub:
root (hd0,0)
kernel /boot/vmlinuz-2.6.20-15-generic root=/dev/sda3 ro quiet splash
initrd /boot/initrd.img-2.6.20-15-generic

I had Drapper Drake installed before (just wiped it) and didn't have any problems installing it. So i'm really puzzled why Grub can't mount my ext3 partition?

---

### Post by happy-and-lost on 2007-04-28
You need to change the line:
root (hd0,0)

to:
root (hd0,*2*)

It's trying to boot Linux from your NTFS partition otherwise

---

### Post by jammeri on 2007-04-28
Yup that did the trick.. Thanks

Doesn't seem really newbie friendly if you have to do it manually. :(

---

### Post by happy-and-lost on 2007-04-28
You don't usually have to, looks like a random glitch on the CD or something like that.

---

### Post by bulldog on 2007-04-28
And you need to modify this selection in the menu.lst as well with the correct UUID for /dev/sda3
```
## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=1e44b9d0-9dff-405d-9fbc-58398539106e ro  ** <---This one**

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,3) **<---And this one as well**
```

And if you have the time ,take a look at your fstab,to see if your boot partition is listed as it should be. 
Remember to pay attention to the UUID's they should be the same in menu.lst and fstab for a particular partition!!

To find the UUID's with the live cd ```
sudo vol_id -u /dev/sda3
```

---

