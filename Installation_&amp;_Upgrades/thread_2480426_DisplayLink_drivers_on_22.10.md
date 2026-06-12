---
title: "DisplayLink drivers on 22.10"
date: 2022-10-29
forum: Installation &amp; Upgrades
---

### Post by benjaminbreeg on 2022-10-29
Has anyone managed to install DisplayLink drivers on Ubuntu 22.10 (ideally without disabling secure boot)? ([I hear]("https://www.displaylink.org/forum/showpost.php?p=94459&postcount=5") that disabling secure boot might just do it.)

---

### Post by benjaminbreeg on 2022-10-31
I can confirm that disabling secure boot does it. Maybe there's a way to manually sign the DL driver in UEFI? Apparently [this page]("https://askubuntu.com/questions/762254/why-do-i-get-required-key-not-available-when-install-3rd-party-kernel-modules") contains a way to do that, but the explanation is quite obscure, and likely obsolete. Anyone care to show us how manual signing is done?

---

