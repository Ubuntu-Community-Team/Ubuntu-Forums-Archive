---
title: "delete 32-bit"
date: 2010-03-14
forum: Installation &amp; Upgrades
---

### Post by Shigoki-linux on 2010-03-14
i dual booted a 32-bit and 64-bit ubuntu 9.10, and im probably stupid for asking, but there IS a way in either to delete the other, right? like if i wana kick off 32-bit i can and visa-versa? thank you!

---

### Post by zvacet on 2010-03-15
Boot in your Ubuntu live CD and delete any version you want.But if you delete one on which is grub installed you will have to [reinstall grub.]("https://help.ubuntu.com/community/Grub2#Reinstalling GRUB 2")

---

### Post by leorolla on 2010-03-15
Best thing is to boot into the install you want to keep, re-install grub to the MBR, and only then you delete the contents of the other partition.

---

