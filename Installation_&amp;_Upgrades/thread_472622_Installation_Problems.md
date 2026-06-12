---
title: "Installation Problems"
date: 2007-06-13
forum: Installation &amp; Upgrades
---

### Post by SAChopper on 2007-06-13
Hi,

I am trying to install Ubuntu on my old PC:

AMD Athlon XP 2000+
512Mb RAM
80Gb HD
2 Optical Drives
1 Floppy Drive (disabled in BIOS)

I am using this iso:  ubuntu-7.04-desktop-i386.iso

I burnt the ISO to a CD-R using Nero, and the CD appears to be totally fine.

When running the installation removing splash and quiet (from F6), everything runs smoothly until:

```

Begin: Mounting root file system... ...
[   48.046092] FDC 0  is a post-1991 82077

```

This appears to freeze here and then:

```

BusyBox v1.1.3 (Debian 1:1.1.3-3ubuntu3) Built-in shell (ash)
Enter 'help' for a list of built-in commands.

/bin/sh: can't access tty; job control turned off
(initramfs) _

```

This is where I'm stuck, does anyone have any ideas on what I could do to fix this?

Thanks,

Matt.

---

### Post by dan_kent on 2007-06-13
on the boot line you can try added 'acpi=off' as these can solve some boot problems

---

### Post by SAChopper on 2007-06-13
It would appear that has worked, theres lots of text everywhere. :D

Thanks for the speedy and accurate response.

---

### Post by SAChopper on 2007-06-13
Ok installation completed, however now after the reboot when it goes to the Ubuntu splash screen the progress bar fills up a couple of pixels and freezes.

Booting into recovery mode seems to be fine until:

```

Begin: Waiting for root file system... ...
[   52.812823] FDC 0 is a post-1991 82077

```

Where it hangs.

Any ideas?

Thanks,

Matt.

---

### Post by barcaxi on 2007-06-14
Hi

I got same problem as SAChopper above after clicking the Ubuntu upgrade button and at reboot :-
- Ubuntu splash screen progress bar stalls afters a few pixels
- minutes later the BusyBox screen with (initramfs) prompt appears

I had to revert to an older version on the kernel to get machine to work again.:(

---

