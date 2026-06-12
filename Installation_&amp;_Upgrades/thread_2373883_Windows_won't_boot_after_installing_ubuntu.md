---
title: "Windows won't boot after installing ubuntu"
date: 2017-10-10
forum: Installation &amp; Upgrades
---

### Post by eiringp on 2017-10-10
[http://paste.ubuntu.com/25713698/ ]("http://paste.ubuntu.com/25713698/")

---

### Post by oldfred on 2017-10-10
Does Ubuntu boot ok from grub menu.
Is it that Windows does not boot from grub menu?
Or can you also not boot Windows from UEFI boot menu, often f10 or f12 check your manual.

What brand/model system?

Grub only boots working Windows.
And main issue is Windows fast start up which really is hibernation. Which grub cannot boot. Or Windows needs chkdsk which then grub will not boot to prevent further damage that chkdsk might not be able to fix.
But report usually shows errors on mounting NTFS if either of those are an issue.

---

