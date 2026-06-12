---
title: "X broken after 12.04-&gt;12.10 upgrade"
date: 2012-12-26
forum: Installation &amp; Upgrades
---

### Post by Wojciech Migda on 2012-12-26
Back in October I attempted a 12.04->12.10 upgrade. It went almost all well but my X became broken.

Now that I execute startx from the console it fails with a segfault (from /var/log/Xorg.0.log):

```
[    31.985] (II) config/udev: Adding input device ImExPS/2 Logitech Wheel Mouse (/dev/input/mouse0)
[    31.985] (II) No input driver specified, ignoring this device.
[    31.985] (II) This device may have been added with another device file.
[    39.887] (EE)
[    39.887] (EE) Backtrace:
[    39.887] (EE) 0: /usr/bin/X (xorg_backtrace+0x49) [0x861cd9]
[    39.887] (EE) 1: /usr/bin/X (0x6ba000+0x1abbc6) [0x865bc6]
[    39.887] (EE) 2: (vdso) (__kernel_rt_sigreturn+0x0) [0x2db40c]
[    39.887] (EE) 3: /lib/i386-linux-gnu/libc.so.6 (0x318000+0x7f6f6) [0x3976f6]
[    39.887] (EE) 4: ?? [0x2106d698]
[    39.887] (EE)
[    39.888] (EE) Segmentation fault at address 0x0
[    39.888]
Fatal server error:
[    39.888] Caught signal 11 (Segmentation fault). Server aborting
[    39.888]
[    39.888] (EE)
Please consult the The X.Org Foundation support
     at http://wiki.x.org
 for help.
[    39.888] (EE) Please also check the log file at "/var/log/Xorg.0.log" for additional information.
[    39.888] (EE)
[    39.900] (II) evdev: Power Button: Close
[    39.900] (II) UnloadModule: "evdev"
[    39.908] (II) evdev: Power Button: Close
[    39.908] (II) UnloadModule: "evdev"
[    39.908] (II) evdev: AT Translated Set 2 keyboard: Close
[    39.908] (II) UnloadModule: "evdev"
[    39.908] (II) evdev: ImExPS/2 Logitech Wheel Mouse: Close
[    39.908] (II) UnloadModule: "evdev"
[    39.938] Server terminated with error (1). Closing log file.

```

Please note the ancient ATI MACH video card I'm using. I have also an unused nvidia card in one of the pci slots, but it hasn't caused any trouble on ubuntu 12.04 nor the gentoo distro I have on the other drive.

Please let me know what else information I can provide to resolve this. I have tried numerous advice from ubuntu fora but none of these worked. I can debug the thing but you'd need to point me to a right direction.

It's a 32-bit system with an intel cpu.

Many thanks in advance,

Wojciech

---

