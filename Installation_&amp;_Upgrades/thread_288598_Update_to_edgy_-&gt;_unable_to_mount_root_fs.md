---
title: "Update to edgy -&gt; unable to mount root fs"
date: 2006-10-30
forum: Installation &amp; Upgrades
---

### Post by Sisko78 on 2006-10-30
After updateing from Dapper Drake to edgy I get the above mentioned kernel panic. The Kernel installed from the system (2.6.17-10) is running fine.

But when I want to use my custom one, the one I Used before with Dapper Drake, I get a Kernel panic. I tried to compile a custom 2.6.17-13 (with and without initrd) but the same problem, and I did not change any parameters in the kernel configuration.
I recognized changes in the kernel line of grub, there I can see an UUID, which is exact the same as the one in /etc/fstab and the System kernel has the same UUID entry, so it has to be the correct root fs, when I try root=(hd0,0), where my boot directory is located, I get the same problem.

Would be nice if you could help me, I'm really frustrated.

Sisko78

---

### Post by Sisko78 on 2006-10-30
I could solve my problem.
During the update the value for root was changed in the grub config file and in fstab (changed to a UUID) and my custom kernel couldnt handle that value, the ubuntu kernel image could handle this UUID, I don't know which Option I should have activated for that.

So I changed the value in menue.lst back to the one before the update.

---

