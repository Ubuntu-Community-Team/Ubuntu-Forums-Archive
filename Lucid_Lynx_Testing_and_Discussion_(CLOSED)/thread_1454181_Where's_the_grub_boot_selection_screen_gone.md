---
title: "Where's the grub boot selection screen gone?"
date: 2010-04-14
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by barisurum on 2010-04-14
Or is it gone with the plymouth integration process? I think plymouth doesn't work for me because I should be able to select kernels with it. Now I can only boot with the latest kernel. The video chip is intel G45 (GMA4500M) on a 64bit emachines e725 laptop. Thanks.

---

### Post by philinux on 2010-04-14
> **barisurum said:**
> Or is it gone with the plymouth integration process? I think plymouth doesn't work for me because I should be able to select kernels with it. Now I can only boot with the latest kernel. The video chip is intel G45 (GMA4500M) on a 64bit emachines e725 laptop. Thanks.

Press the shift key at boot up. See link in sig for grub2.

---

### Post by barisurum on 2010-04-14
Oh so its hidden eh? Allright but it would be better to give some info about it on the boot screen to the user :) Thanks philinux!

---

### Post by dino99 on 2010-04-14
even with multiple boots i've had grub menu issue with kernel 32.20
Latest 32.21 kernel + grub-mkconfig + update-grub brings menu to show up again, but bad grub config again with this weird deprecated vga=xxx that grub-mkconfig build (no grub1, all purged)

So i've edited /etc/default/grub to remove that vga=xxx thing, and made a update-grub again, now it's ok.

---

