---
title: "UbuntuStudio Boot Problem"
date: 2008-02-01
forum: Installation &amp; Upgrades
---

### Post by ScoLgo on 2008-02-01
Hi,
Downloaded Alternate DVD iso and Ubuntu Studio installs without a hitch. However, on first boot, the system immediately hangs with 'Error 15: File not found - Press any key to continue...'

System Specs...
Intel Core 2 Duo E6750
ASRock 4Core1333 MB
MSI NX8500GT TD512EH Video Card
Hoontech/ST Audio DSP2000 PCI Audio
4GB RAM
Booting from 500GB WD IDE drive (using swappable boot drives instead of dual-boot)
Additional 500GB Samsung SATA drive installed


Thanks in advance,
--
ScoLgo

Follow Up:  Found the fix. Grub was looking at (hd1,0). Changed it to hd0,0) and I'm in!

---

### Post by doddo on 2008-02-02
Hello!

This sounds like a GRUB issue to me

Are you familiar with grub commands???

what you want to do here is to press ESC on boot to load grub

Then go to ur kernel line (the one on top should be the one ur booting fron) and press E

Then you will see something similar to this
```

root (hd0,0)
kernel=/vmlinuz(the name of ur kernel) root=/dev/sdXX(the partition mounted as /) and some other parameters
initrd=/the name of ur initrd.img
```

So what I think you should try is to fist select the kernel line and press e again. Then use arrows to navigate to the kernel= part, remove the stuff between kernel= and  root =D

then you should try

```
kernel=/<HIT TAB A LOT OF TIMES> boot=/d...
```

What do you see??

do the same thing for the initrd.img part

what do you see??

---

