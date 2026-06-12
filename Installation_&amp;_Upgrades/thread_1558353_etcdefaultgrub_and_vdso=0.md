---
title: "/etc/default/grub and vdso=0"
date: 2010-08-22
forum: Installation &amp; Upgrades
---

### Post by davidmaxwaterman on 2010-08-22
Hi,

When I try to start scratchbox, I get the following error :

> Host kernel has vdso support (which is uncompatible with SB)
You can fix this with either: 
  echo 0 > /proc/sys/vm/vdso_enabled
or
  add 'vdso=0' to the kernel parameters


So, I'm trying to do the second option, and, in the past, I've added it to the /etc/default/grub file with 'GRUB_CMDLINE_LINUX="vdso=0"', but that has no effect (since my 10.4) upgrade.

Is there some other place I should put it?

I notice also in that file, I have added 'GRUB_GFXPAYLOAD_LINUX=1366x768' and 'GRUB_GFX_MODE=1366x768', but neither of these seem to have any effect either.

Help?

Max.

---

