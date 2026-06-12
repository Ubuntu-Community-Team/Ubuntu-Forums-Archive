---
title: "Update to kernel 2.6.32-26-generic-pae killed my nvidia-current driver"
date: 2010-11-24
forum: Installation &amp; Upgrades
---

### Post by YuiDaoren on 2010-11-24
Tonights update from -25 to -26 seems to have broken my video driver.

On re-installing nvidia-current under -26, it reports that it has skipped building the kernel module as "the kernel source does not appear to be installed".

-25 still functions fine, and re-installing nvidia-current while running that kernel gets a module compile for it, but the above message for -26.

I have tried re-installing linux-generic-pae (sudo aptitude reinstall linux-generic-pae) to no effect.

Anyone have a spare clue for me? I am at a loss.


EVGA nVidia 9800gt 512MB
AMD Phenom II X4 955 (3.2Ghz)
AMD 770 north bridge, AMD SB710 south
4MB DDR3 1333

---

### Post by YuiDaoren on 2010-11-24
There is something magical about posting a plea for help that makes the brain come up with fresh approaches.

I looked about in synaptic and discovered that - [SIZE="1"][FONT="Garamond"]and I really can't explain how I did this[/FONT][/SIZE] - the meta-package linux-headers-generic-pae was no longer installed, so the headers for the new kernel never got installed, and thus no module could be compiled. Reinstalling the headers meta-package then reinstalling nvidia-current brought everything back to happy-town.

Thanks to anyone who peeked in this thread to help. :D

---

