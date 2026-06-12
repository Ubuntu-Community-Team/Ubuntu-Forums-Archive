---
title: "liveCD don't boot : &quot;attempt to access beyond end of device&quot;"
date: 2007-08-29
forum: Installation &amp; Upgrades
---

### Post by elapouya on 2007-08-29
I bought a new PC :
Intel Q6600
Motherboard : MSI (do not know wich one)
2 LG drives :
  HL-DT-ST DVDRAM GSA-H42N ATA Device
  HL-DT-ST DVD-ROM GDR8163B ATA Device
Nvidia 8800 GTS 320Mo,
3GB RAM
RAID0 (2x500 GB stripped)

But I cannot boot the Ubuntu Live CD : I got :

```

...
attempt to access beyond end of device
sda: rw=0, want=1912518658, limit=976773168

BusyBox v1.1.3 (Debien 1:1.1.3-5ubuntu1) Built-in shell (ash)
Enter 'help' ...

/bin/sh:can't access tty; jobcontrol turned off
(initramfs)
```

I tried many Live CD (Alternate CD, 6.10 etc...) still the same thing

I tried the workaround : "break=top" + modprobe piix (also tried to modprobe all modules)
but it does not help.

I also tried OpenSuse, gentoo and fedora 7 : for all, the boot begins (linux welcome screen), but after a while, linux says that the boot cdrom has not been found.

Any Idea ?

---

### Post by elapouya on 2007-08-30
By replacing the DVD drive by another one which was able to boot Ubuntu in another PC,
the problem still occurs.

Could you help me ?

---

