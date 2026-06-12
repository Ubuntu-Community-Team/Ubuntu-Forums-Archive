---
title: "X server won't start with Ubuntu Studio 7.04 and Intel graphics card"
date: 2007-05-29
forum: Installation &amp; Upgrades
---

### Post by jonbate on 2007-05-29
Hi all, I'd be very grateful if someone could help me with the following...

Just installed Ubuntu Studio 7.04 on a Fujitsu Siemens Amilo laptop. One hard drive with three partitions- Windows Vista (NTFS), Ubuntu Studio (ext3) and Linux swap. Installed GRUB to the ext3 partition and used EasyBCD to chainload it from the Vista bootloader.

When starting Ubuntu for the first time the X server fails to start. Here's the last few lines of the X server output:

```
(II) VESA(0): Total memory:123 64kB banks (7872 kB)
(II) VESA(0): Generic monitor: Using hsync range of 28.00-64.00kHz
(II) VESA(0): Generic monitor: Using vrefresh range of 43.00-60.00Hz
(II) VESA(0): Not using mode “1280x800” (no mode of this name)
(II) VESA(0): Not using mode “1280x768” (no mode of this name)
(II) VESA(0): Not using mode “1280x720” (no mode of this name)
(II) VESA(0): Not using built-in mode “1024x800” (no mode of this name)
(II) VESA(0): Not using built-in mode “800x600” (no mode of this name)
(II) VESA(0): Not using built-in mode “640x480” (no mode of this name)
(WW) VESA(0): No valid modes available, trying less strict filter...

Backtrace:
0: / usr/bin/X(xf86SigHandler+0x81)  [0x80c5d91]
1: [0xffffe4207]
2: /usr/bin/X(InitOutput+0x9aa) [0x80a5b9a]
3: /usr/bin/X(main+0x276) [0x807456b]
4: lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xdc) [0xb7d08ebc]
5: /usr/bin/X(FontFileCompleteXLFD+0x1e1) [0x8073ab1]

Fatal server error:
Caught signal 11. Server aborting
```

My graphics card is an Intel 945GM and it looks to me like the problem is the one described here:
[https://help.ubuntu.com/community/FixVideoResolutionHowto#head-0e3051713171cb5d1bf49dc2dc7bea24eb9ed83e](https://help.ubuntu.com/community/FixVideoResolutionHowto#head-0e3051713171cb5d1bf49dc2dc7bea24eb9ed83e).

However, I can't apply the fix described because running gedit gives me a "cannot open display:" error message.

Does anyone know a work around for this so I can repair my X server?

Thanks in advance!

---

### Post by jonbate on 2007-05-29
Nevermind, reconfiguring the xserver fixed it... for some reason it wasn't using the i810 drivers.

---

