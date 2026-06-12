---
title: "Not booting to the right kernel after upgrade to Gutsy"
date: 2007-10-19
forum: Installation &amp; Upgrades
---

### Post by MrWookie on 2007-10-19
Well, I tried updating to Gutsy today, and it looked like it worked.  However, when I tried to boot, I looked at GRUB, and I only saw the 2.6.20-16 and the 2.6.20-15 kernels, the ones I had installed when I was running 7.04.  The new kernel did not appear in the list, but poking around in installed packages, it looks like it's there somewhere.  If I boot to the -16 kernel, then the restricted devices manager won't load to let me use my nVidia graphics card.  Any ideas about how to fix this?  Thanks.

---

### Post by MrWookie on 2007-10-19
As an update to this, here's the relevant information in /boot/grub/menu.lst:

```
title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=/dev/md3 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=/dev/md3 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, kernel 2.6.20-15-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=/dev/md3 ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet

title		Ubuntu 7.10, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=/dev/md3 ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
```

When I saw this in there, I was very surprised, because the GRUB menu I actually see contains no references to Ubuntu 7.10 nor does it contain the entries for the 2.6.22 kernel.

---

### Post by MrWookie on 2007-10-19
Well, as I've been poking around some more, I'm only left more baffled by this.  The grub menu that loads on boot is the one for my previous Ubuntu install, 7.04.  It displays an entry for 2.6.20-16 kernel which no longer exists on my system -- at least, it's no longer found in /boot.  The contents of my /boot directory are

```
abi-2.6.20-15-generic         initrd.img-2.6.22-14-generic.bak
abi-2.6.22-14-generic         memtest86+.bin
config-2.6.20-15-generic      System.map-2.6.20-15-generic
config-2.6.22-14-generic      System.map-2.6.22-14-generic
grub                          vmlinuz-2.6.20-15-generic
initrd.img-2.6.20-15-generic  vmlinuz-2.6.22-14-generic
initrd.img-2.6.22-14-generic
```

Anyway, my current grub boots to the 2.6.20-16 kernel by default, and somehow linux comes up. uname -a says it's even running the 2.6.20-16 kernel.  There's an error message as it's booting up that it can't find the 2.6.20-16 kernel, but boot continues on and makes it.  

I've rerun update-grub, and it doesn't change my menu.lst.  I have no idea why the menu.lst file currently in /boot/grub doesn't seem to be the one that's being used, though.

---

