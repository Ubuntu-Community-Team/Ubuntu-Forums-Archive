---
title: "Failing to install DualBoot in UEFI mode"
date: 2019-12-04
forum: Installation &amp; Upgrades
---

### Post by allusferatu on 2019-12-04
Hello, I'm a newbie in the linux world and I was trying to install a dualboot using windows 10 and ubuntu 18.03.  Apparently my BIOS supports UEFI boot, since i installed the Windows 10 in UEFI mode and My Windows system information says that it is an UEFI Bios[IMG]https://drive.google.com/file/d/1hV2JKyM4kTguOQZGnJ4oKp7QPxMebtyt/view?usp=sharing[/IMG] (as shown below).
 [ATTACH=CONFIG]284553[/ATTACH][IMG]https://drive.google.com/file/d/1hV2JKyM4kTguOQZGnJ4oKp7QPxMebtyt/view?usp=sharing[/IMG]


The problem is that:
 [ATTACH=CONFIG]284552[/ATTACH]
I've also made sure that secure boot and fast boot are disabled. What can i do to fix this ?

---

### Post by oldfred on 2019-12-04
In your UEFI boot menu, you should have two boot entries (if BIOS allowed) and UEFI Secure Boot is off. If Secure Boot is on, you should not get a BIOS boot option.
One is clearly UEFI, something like [noparse]UEFI:PMAP[/noparse]. My system normally shows PMAP, others may show name or label of flash drive. If just PMAP that would be a BIOS boot.

Most systems also need UEFI settings to allow USB boot and USB full support.
Boot of USB flash drive is separate from default boot settings of an installed system.

What brand/model system? Is it just Biostar? What video card/chip?
Have you updated UEFI to latest available from vendor?
Some brands/models require boot parameters.

---

### Post by allusferatu on 2019-12-04
I've solved the problem. You were right, thanks!

---

