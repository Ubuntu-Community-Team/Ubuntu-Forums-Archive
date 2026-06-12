---
title: "Boot Flag Installer"
date: 2010-06-25
forum: Installation &amp; Upgrades
---

### Post by xMbx on 2010-06-25
Hello,

i got a tiny problem. How to change the Boot Flag within the installer for RAID partitions to "on". I tried nearly any key, it didn´t seems to work.

3x 2TB with RAID 5 is the idea.

Thanks.

---

### Post by darkod on 2010-06-25
Grub doesn't use the boot flag. Any particular reason to set it?

And you have to use the Alternate Install CD image for RAID install, you are aware of that right? Although there are workarounds to use the LiveCD too, but grub2 installation is not complete.

---

### Post by xMbx on 2010-06-25
> **darkod said:**
> Grub doesn't use the boot flag. Any particular reason to set it?

And you have to use the Alternate Install CD image for RAID install, you are aware of that right? Although there are workarounds to use the LiveCD too, but grub2 installation is not complete.

Well i tried Hard Server, Lucid Server and Lucid Server Alt.
It doesn´t seems to find the system without the flag on Hardy.

But why does the boot flag won´t change ?

---

