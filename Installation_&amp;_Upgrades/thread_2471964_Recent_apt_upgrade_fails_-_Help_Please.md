---
title: "Recent apt upgrade fails - Help Please"
date: 2022-02-14
forum: Installation &amp; Upgrades
---

### Post by gourmetsaint on 2022-02-14
I get the following:
zstd: error 25 : Write error : No space left on device (cannot write compressed block)
E: mkinitramfs failure zstd -q -19 -T0 25
update-initramfs: failed for /boot/initrd.img-5.11.0-37-generic with 1.
dpkg: error processing package linux-firmware (--configure):
 installed linux-firmware package post-installation script subprocess returned error exit status 1
Errors were encountered while processing:
 linux-firmware
ZSys is adding automatic system snapshot to GRUB menu
E: Sub-process /usr/bin/dpkg returned an error code (1)

I am using zfs on boot and root. I culled most of old snapshots.

However, bpool shows:
NAME    SIZE  ALLOC   FREE  CKPOINT  EXPANDSZ   FRAG    CAP  DEDUP    HEALTH  ALTROOT
bpool  1.88G  1.71G    169M        -         -                 55%    91%  1.00x    ONLINE  -

What else ban I clean up? Can I increase bpool/partition sizes? I'm using ZFS mirrored NVME drives (ie partitioning identical on both...)

Any help appreciated.

---

### Post by gourmetsaint on 2022-02-14
Found the issue. /boot full of old kernels etc.
Purged and ruinning now

---

### Post by MAFoElffen on 2022-02-14
ZFS-on-root uses it's own boot partition, which that error tells us that that partition seems to be full.

During normal use, that partition should be sufficient size, if you have been doing normal maintenance over time... (Removing old kernels.)

It still boots to the system right? If not, I'll provide instruction on how to mount and chroot into the system from a LiveCD. it's much easier if it still boots. LOL

In a nut shell, 
```

sudo apt autoremove

```
Try that first to see if that does anything without returning an error on broken packages or dpkg being interrupted...

EDIT... LOL. See, while I was posting my reply, you found out what I saying was true... Yes, too many old kernels is the culprit.

---

