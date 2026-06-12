---
title: "Any issues dual booting Fiesty Fawn and Windows XP OEM"
date: 2007-06-14
forum: Installation &amp; Upgrades
---

### Post by justinae on 2007-06-14
I need windows XP to run some CAD software for work, unfortunately. Is there any issue with dual booting Windows XP that is an OEM version? Has anyone successfully done that?

many thanx

---

### Post by carytid9 on 2007-06-14
Yes, I have done just that. I use Symantec's Boot Magic as the multi boot agent, purely because I have got used to it. The XP installation will overwrite the MBR, so you'll need to run grub-install (see the man page) before installing XP, to install Grub in your Linux root partition. If you then run Boot Magic, it will locate the Grub partition, and enable you  to boot into  XP or Linux on startup.

If the Linux installation  is done when XP is already installed, you can use the multiboot menu which is part of a normal Ubuntu install. Grub must be installed in your Ubuntu root partition, NOT the default, which is the MBR.

Good luck!

---

