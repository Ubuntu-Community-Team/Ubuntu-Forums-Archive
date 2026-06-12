---
title: "grub dissappear after autoupgrade of bios/uefi. windows wants me back"
date: 2022-12-12
forum: Installation &amp; Upgrades
---

### Post by oma80 on 2022-12-12
I've had grub dissappear before, fixed it in uefi boot order, but it doesn't seem to work this time.

The boot-repair hangs forever, but here is it's recommendation

[https://paste.ubuntu.com/p/FZVHTvTXyr/](https://paste.ubuntu.com/p/FZVHTvTXyr/)

on lenovo x1. Windows completely removed. On a reboot I had an autoupdate of bios with lots of beeping. Once done, my grub isn't loaded and it complains that windows/system32 isn't found. Can't windows give me a break already, I want Ubuntu.

Thanks for any help.

---

### Post by tea for one on 2022-12-12
[COLOR="#0000FF"]Line 104[/COLOR]  - nvme0n1p1	: hidenESP,	part-has-no-fstab,	no-nt,	no-winload,	recovery-or-hidden,	no-bmgr,	notwinboot

I imagine that this means the ESP is hidden and therefore grub could not operate perfectly.
Can you boot into a live Ubuntu session, open Gparted and double check the ESP flags.

---

