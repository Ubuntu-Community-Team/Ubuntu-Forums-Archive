---
title: "Can't boot into recovery mode"
date: 2007-12-24
forum: Installation &amp; Upgrades
---

### Post by Jugney on 2007-12-24
Hey everyone,

I can't get into recovery mode to configure Xorg. When I try to boot into Recovery Mode, it freezes at the following lines:

[ 0.552000] Enabling IO-APIC IRQ
[ 0.552000] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1

When I grappled with getting my nVidia drivers working on my first install I could get around this by booting from my text install CD (LiveCD didn't work), then pressing CTRL+ALT+DELETE to reboot. I took out the CD to get the regular boot menu and then I could get into recovery mode. But that doesn't work anymore.

Please help! I want my Ubuntu back!

Jugney

---

### Post by Partyboi2 on 2007-12-24
What happens if you boot with noapic added to the boot options?
Boot the pc and when grub is loading press "Esc" then select the kernel and press "e"
you will see a line starting with Kernel something, like this:
>  kernel    /boot/vmlinuz-2.6.12-10-k7 root=/dev/hdb1 ro quiet splash
after splash add noapic then press b
If that works then you can add it to the grub menu.lst

---

### Post by Jugney on 2007-12-25
Thank you! That did it and I was able to get things back working.

---

