---
title: "all kernels after 2.6.15-23"
date: 2006-09-28
forum: Installation &amp; Upgrades
---

### Post by dannytherocker on 2006-09-28
Hi everybody,

Own 2 pcs: an old PIII, 550 mhz and a Acer Aspire 1350 with 1 GB ram. No trobules at all with the 1st....My real trouble is with the 2nd! Only kernel 2.6.15-23 works fine, the others don't! and it's always the same thing: external usb devices are not recognised by the system, so mouse, extern hd, ext dvd burner do not exist for ubuntu!
Kernel 2.6.15-27 sometimes works, sometime does not....for examples I can use pc for 2 hrs and everything's fine but helter skelter, usb devices stop and O have to..."init 6"!!!
Yesterday, just compiled kernel 2.6.17 emission 8 for splashutils using: does not work from the beginning....

Consider that 2 ports (total 4) don't work...Think it'a an hardware prob!

What happens to my pc??
Thanks in advance
e-maj

PS. I'm desperate....:-(

---

### Post by sgbeamer on 2006-09-28
This has been going on for a while and it only happens on certain hardware.  I'm not sure why.  I did a vanilla kernel with the older settings (from 2.6.15-23) and that works.  The Ubuntu kernel has troubles on my Asus motherboard but works fine on my two HP's

---

### Post by dannytherocker on 2006-09-28
> **sgbeamer said:**
> This has been going on for a while and it only happens on certain hardware.  I'm not sure why.  I did a vanilla kernel with the older settings (from 2.6.15-23) and that works.  The Ubuntu kernel has troubles on my Asus motherboard but works fine on my two HP's

how did you export your settings from ...15-23 to the new vanilla kernel?? maybe "cp /boot/config-your_kernel_2.6.15-23 .config" ??? I would do the same with mine....

---

