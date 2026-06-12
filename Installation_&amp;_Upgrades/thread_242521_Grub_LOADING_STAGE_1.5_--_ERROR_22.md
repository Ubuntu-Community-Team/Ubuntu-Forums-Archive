---
title: "Grub LOADING STAGE 1.5 -- ERROR 22"
date: 2006-08-23
forum: Installation &amp; Upgrades
---

### Post by loxish on 2006-08-23
So, I was dual booting Windows XP and Ubuntu, I accidently deleted the partition that I had Ubuntu on and now, when I boot the machine, it stalls at boot with the dialog:

GRUB LOADING STAGE 1.5

Loading Grub...
ERROR 22.

Anyone have any idea how I can nuke this issue?

---

### Post by loxish on 2006-08-23
Figured it out, used Windows XP Recovery console and used the command "fixmbr" which resets the master boot record, it fixed it.

---

