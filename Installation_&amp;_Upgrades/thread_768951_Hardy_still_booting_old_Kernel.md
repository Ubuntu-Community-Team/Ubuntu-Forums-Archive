---
title: "Hardy still booting old Kernel"
date: 2008-04-26
forum: Installation &amp; Upgrades
---

### Post by dmj99 on 2008-04-26
I upgraded to Hardy (from the alternate CD).  I kept my old menu.lst file, because I had made a lot of modifications.  My menu.list file reads

```
title Ubuntu 7.10, kernel 2.6.22-14-generic
root (hd0,2)
kernel /boot/vmlinuz-2.6.22-14-generic root=UUID=b710542e-e4a7-4b01-809b-3337bcf585e4 ro quiet splash
initrd /boot/initrd.img-2.6.22-14-generic
quiet
```

If I edit the kernel and initrd lines to 2.6.24-16, I get a white screen after gnome starts to boot up.  I've checked that the new kernel is in the boot folder.

It would be nice to use the newer kernel.  Any ideas?  Thanks

---

