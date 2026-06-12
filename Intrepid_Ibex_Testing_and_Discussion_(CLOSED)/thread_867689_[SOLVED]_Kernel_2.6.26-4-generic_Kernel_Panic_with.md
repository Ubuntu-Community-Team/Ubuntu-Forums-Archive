---
title: "[SOLVED] Kernel 2.6.26-4-generic Kernel Panic with RAID-0"
date: 2008-07-23
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by ViRMiN on 2008-07-23
I've previously installed 7.10 and 8.04 following the FakeRaid HowTo ([https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)).

A couple of days ago I upgrade my 8.04 installation to 8.10 Alpha 2, and whilst I can work quite happily using kernel 2.6.24-19, version 2.6.26-4 results in:

```
"Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(0,0)
```

I think it has something to do with my RAIDed installation, as, if I boot in recovery using this kernel, I see errors mentioning the /dev/mapper/nvidia_ihegheeh devices which are setup by dmraid.  Just to complicate things a bit more, all my partitions are XFS apart from /boot which is ext3.

Any ideas?  I'll try and make a note of the errors/warnings running up to the panic event...

---

### Post by ViRMiN on 2008-07-24
Cause of the fault, missing "initrd" entries in /boot/grub/menu.lst:

```
title        Ubuntu intrepid (development branch), kernel 2.6.26-4-generic
root        (hd0,0)
kernel        /vmlinuz-2.6.26-4-generic root=/dev/mapper/nvidia_ihegheeh3 ro quiet splash

title        Ubuntu intrepid (development branch), kernel 2.6.26-4-generic (recovery mode)
root        (hd0,0)
kernel        /vmlinuz-2.6.26-4-generic root=/dev/mapper/nvidia_ihegheeh3 ro single

title        Ubuntu intrepid (development branch), kernel 2.6.24-19-generic
root        (hd0,0)
kernel        /vmlinuz-2.6.24-19-generic root=/dev/mapper/nvidia_ihegheeh3 ro quiet splash
initrd        /initrd.img-2.6.24-19-generic

title        Ubuntu intrepid (development branch), kernel 2.6.24-19-generic (recovery mode)
root        (hd0,0)
kernel        /vmlinuz-2.6.24-19-generic root=/dev/mapper/nvidia_ihegheeh3 ro single
initrd        /initrd.img-2.6.24-19-generic

title        Ubuntu intrepid (development branch), memtest86+
root        (hd0,0)
kernel        /memtest86+.bin

```

---

### Post by ViRMiN on 2008-07-24
BTW, the full text was:

```

VFS: Cannot open root device "mapper/nvidia_ihegheeh3" or unknown-block(0,0)
Please append a correct "root=" boot options; here are the available partitions:
Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(0,0)

```

---

### Post by euxneks on 2008-10-21
This helped me immensely thank you very much..

My Grub menu.lst now:


```
title       Debian GNU/Linux, kernel 2.6.27-7-generic
root        (hd1,0)
kernel      /boot/vmlinuz-2.6.27-7-generic root=UUID=dafc1235-771c-44fc-9fae-190ce97296cb ro quiet splash
**initrd      /boot/initrd.img-2.6.27-7-generic**
savedefault

title       Debian GNU/Linux, kernel 2.6.27-7-generic (recovery mode)
root        (hd1,0)
kernel      /boot/vmlinuz-2.6.27-7-generic root=UUID=dafc1235-771c-44fc-9fae-190ce97296cb ro single
**initrd      /boot/initrd.img-2.6.27-7-generic**
savedefault
```

---

