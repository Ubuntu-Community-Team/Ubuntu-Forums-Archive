---
title: "kernel upgrade problem: can't find image in /boot/"
date: 2010-02-12
forum: Installation &amp; Upgrades
---

### Post by Uhuabin on 2010-02-12
Hi, I'm using Karmic. tried to upgrade my kernel to 2.6.32.20 by apt-get. no error message reported. but somehow i can't find the linux header image in /boot/. and the grub won't update after restart. anyone can help me? thanks a lot.

---

### Post by ratcheer on 2010-02-12
Can you still boot to an older kernel? If yes, try "sudo update-grub" and see if that fixes it.

Tim

---

### Post by Uhuabin on 2010-02-12
> **ratcheer said:**
> Can you still boot to an older kernel? If yes, try "sudo update-grub" and see if that fixes it.

Tim

Hi Tim, thanks for reply. I tried update-grub but it could not find the new kernel, just find the older one. so the grub menu remain unchanged.

---

