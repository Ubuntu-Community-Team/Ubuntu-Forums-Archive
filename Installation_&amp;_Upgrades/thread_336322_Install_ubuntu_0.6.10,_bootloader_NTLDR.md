---
title: "Install ubuntu 0.6.10, bootloader NTLDR"
date: 2007-01-11
forum: Installation &amp; Upgrades
---

### Post by tejvenim on 2007-01-11
I **highly ** prefer NTLDR over GRUB because it don't make changes to the MBR, so I can easily uninstall ubuntu 0.6.10.

Is there away to install ubuntu 0.6.10 so that the bootloader is NTLDR?

---

### Post by computergroove on 2007-01-11
So your question is "Does Microsoft support Linux?" I dont really know but my guess is no.

---

### Post by arnieboy on 2007-01-11
> **tejvenim said:**
> I **highly ** prefer NTLDR over GRUB because it don't make changes to the MBR, so I can easily uninstall ubuntu 0.6.10.

Is there away to install ubuntu 0.6.10 so that the bootloader is NTLDR?
Grub can be written on to an active bootable partition (does not necessarily have to overwrite MBR)

---

### Post by vmikalinis on 2007-01-11
I think there are many atricles on the web about this such as [http://jaeger.morpheus.net/linux/ntldr.php](http://jaeger.morpheus.net/linux/ntldr.php)

I'm personally using grub with windows xp media ed and unbuntu 6.10(64).  It works fine with this setup, but I will be looking into flipping the options to list windows as the first OS, even though I use them equally.

---

