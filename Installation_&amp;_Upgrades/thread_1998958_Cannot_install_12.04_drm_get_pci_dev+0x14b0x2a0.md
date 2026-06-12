---
title: "Cannot install 12.04 drm_get_pci_dev+0x14b/0x2a0"
date: 2012-06-07
forum: Installation &amp; Upgrades
---

### Post by GunNam on 2012-06-07
My system:
Dell XPS 8300
Intel Core i7-2600 (8BM Cache, 3.4GHz)
NVidia GTX 420 1GB DDR3


I have tried both the Ubunutu 12.04LTS 32bit & 64bit installations and I am getting the same error (I have also tried another variant - Linux Minx with similar, if not exact results).

When I try to install Ubuntu, I get the following screen and my computer is frozen:

drm_get_pci_dev+0x14b/0x2a0 [drm]
? _raw_spin_lock_irqsave+0x2d/0x40
nouveau_pci_probe+0xd/oxf [nouveau]
local_pci_probe+0x47/0xb0
pci_device_probe+0x68/0x90
? sysfs_create_link+0x17/0x20
etc...

I am installing from the CD-ROM if that matters. (booting into CDRom with the installation disk).

---

### Post by marinara on 2012-06-07
what's the exact error, or the last line? or what happens?
Do you get a thin line, or a black screen? or a blinking cursor?

---

### Post by sanderj on 2012-06-07
Have you googled "nouveau_pci_probe+0xd/oxf [nouveau]"? I did, and it looks like some bug in a linux kernel.

So, worth a try:
older Ubuntu version (11.10)
do not use nouveau (I don't know how to do that: maybe something to set at boot time (VESA?)), and then install proprietary driver.
swap Nvidia card for non-Nvidia ;-)

---

### Post by GunNam on 2012-06-07
> **marinara said:**
> what's the exact error, or the last line? or what happens?
Do you get a thin line, or a black screen? or a blinking cursor?

The last line of all this gibberish (to me anyway) is:
sysenter_do_call+0x12/0x28
_

A blinking cursor at the bottom... but frozen, can't do anything at this point.

---

### Post by GunNam on 2012-06-07
> **sanderj said:**
> Have you googled "nouveau_pci_probe+0xd/oxf [nouveau]"? I did, and it looks like some bug in a linux kernel.

So, worth a try:
older Ubuntu version (11.10)
do not use nouveau (I don't know how to do that: maybe something to set at boot time (VESA?)), and then install proprietary driver.
swap Nvidia card for non-Nvidia ;-)

Before I tried Ubuntu, I installed Linux Mint.  It went all the way through the install, then I had to go into compatibility mode to install the proprietary NVidia driver (recommended & current driver).  Afterwards, it would not boot into the X Server.  I get the same error when trying to install Ubuntu 12.04, which is partly included on my initial post.

---

