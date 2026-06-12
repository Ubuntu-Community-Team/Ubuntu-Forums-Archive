---
title: "Difficulty Re-Installing GRUB"
date: 2007-11-28
forum: Installation &amp; Upgrades
---

### Post by ErusGuleilmus on 2007-11-28
I recently had to re-install Windows, and GRUB was consequently destroyed. This is how I am trying to reinstall it through a live cd session in terminal:

```
sudo grub

find /boot/grub/stage1 (The out put is: (hd0,2))

root (hd0,2)

setup (hd0,2)
```

This is where the problems start. Here is the out put after the last command:

```
Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0,2)"... failed (this is not fatal)
 Running "embed /boot/grub/e2fs_stage1_5 (hd0,2)"... failed (this is not fatal)
 Running "install /boot/grub/stage1 (hd0,2) /boot/grub/stage2 p /boot/grub/menu
.lst "... succeeded
Done.

```

At first I assumed that when it comments "this is not fatal" that everything was successful, Until I rebooted and my computer went straight to Windows with no sign of GRUB. Any suggestions? Thanks.

---

### Post by rsambuca on 2007-11-28
You need to install grub to the mbr, not (hd0,2).  Therefore, the last step you want to

setup (hd0)

---

### Post by ErusGuleilmus on 2007-11-28
Thank you, rsambuca!! Your advice worked great, and I am typing this from Ubuntu. Thanks again.

---

