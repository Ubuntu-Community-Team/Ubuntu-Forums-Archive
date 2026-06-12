---
title: "Changing partition broke install"
date: 2011-07-08
forum: Installation &amp; Upgrades
---

### Post by Luke M on 2011-07-08
I changed partitions (partition X is now partition X+1) and can no longer boot. I get thrown into grub rescue. But even if I get past that, it still doesn't boot. (I can't see why because it's using an unsupported graphics mode by default, but that's another gripe). I would prefer an installation which is not fragile to changes in partition numbers or drive numbers. It's not 1975 any more, can't we use meaningful names instead of 0, 1, 2?

---

### Post by Luke M on 2011-07-08
> **Luke M said:**
> I changed partitions (partition X is now partition X+1) and can no longer boot. I get thrown into grub rescue. But even if I get past that, it still doesn't boot. (I can't see why because it's using an unsupported graphics mode by default, but that's another gripe).

 Strange, I used the vga=791 option so I could see what was happening and this time it booted (after first going through the grub rescue "set prefix=, set root=, insmod normal, normal" incantation).

---

### Post by dino99 on 2011-07-08
sudo update-grub

---

