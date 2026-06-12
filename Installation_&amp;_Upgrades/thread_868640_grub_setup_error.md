---
title: "grub setup error"
date: 2008-07-24
forum: Installation &amp; Upgrades
---

### Post by ayet on 2008-07-24
this is what i always do to re-install grub now there seems to be a problem, whenever i dual boot to winxp.



grub> find /boot/grub/stage1
 (hd0,5)

grub> root (hd0,5)

grub> setup (hd0)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...  16 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd0) (hd0)1+16 p (hd0,5)/boot/grub/stage2
/boot/grub/menu.lst"... failed

Error 12: Invalid device requested

grub>

---

### Post by ayet on 2008-07-24
is there any solution to this?

---

