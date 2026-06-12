---
title: "Dual Boot. Every Time I launch Windows I lose my Grub boot menu"
date: 2021-10-15
forum: Installation &amp; Upgrades
---

### Post by fparri on 2021-10-15
As I wrote, every time I launch Windows I lose my Grub boot menu and I need to use boot-repair to fix it. Anyone can help me solve it more permane

---

### Post by oldfred on 2021-10-15
What brand/model system?
Windows with updates, will usually reset boot order so Windows is first, but grub does that with updates & makes Ubuntu entry first.

Grub uses efibootmgr to set boot order. See:
man efibootmgr and the -o option.

But some systems like HP, do not seem to recognized the changes using efibootmgr. Users have updated UEFI (may not be required) and then in UEFI settings (not UEFI boot menu) change boot order.

---

