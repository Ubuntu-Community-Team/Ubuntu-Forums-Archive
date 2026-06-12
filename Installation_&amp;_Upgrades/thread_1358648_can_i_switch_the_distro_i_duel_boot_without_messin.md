---
title: "can i switch the distro i duel boot without messing with GRUB"
date: 2009-12-18
forum: Installation &amp; Upgrades
---

### Post by cain071546 on 2009-12-18
ok so i can switch distros but do i have to mess with the grub loader when i do?????   also i installed inside windows via Wubi not from disk, does that effect anything?

---

### Post by oldfred on 2009-12-18
If you have wubi you do not have grub installed in the MBR. You are actually booting windows and then choosing whether to continue with windows or start the wubi program. wubi is just a program running in windows like any other windows program except it takes over and runs like an ubuntu install.

---

### Post by avtolle on 2009-12-18
As I understood the question, the op wishes to switch from Windows to Ubuntu (installed using Wubi) or vice versa without closing one down and booting the other. The answer is no, assuming he has mistaken the Windows bootloader for Grub. If this this what is desired, then running one inside the other via a virtual machine would be the only way I know to do it.

BTW, if a "true" dual boot (separate partitions, etc.) is what is desired, the answer is still "no".

---

