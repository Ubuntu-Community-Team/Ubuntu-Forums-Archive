---
title: "Upgrading a Dual-Boot Computer"
date: 2005-08-12
forum: Installation &amp; Upgrades
---

### Post by wingnut2292 on 2005-08-12
Hello to everyone in the Ubuntu Community!

I currently use a dual-boot Win2k / Ubuntu 5.04 configuration.  However after a problem with Windows Update Windows 2000 takes for ever to boot up. So instead of trying to debug Win2k, I'd like to upgrade to XP (since my Athalon 900 MHz + 384 MB. Prob won't run Vista, from early reports. Not to mention that most Vista features are being moved to XP, too) I know that by Installing XP I'll whipe out the MBR.  What should I do to preserve/restore it so I can run XP and Ubuntu?

---

### Post by kosmic on 2005-08-12
install windows normaly, and after the instalation is complete insert your Ubuntu Install CD and start it in rescue mode, or use a live cd and then use the command

Grub-install  to install Grub to the MBR again.

---

### Post by Gav-UK on 2005-08-13
[QUOTE=wingnut2292]Hello to everyone in the Ubuntu Community!

I currently use a dual-boot Win2k / Ubuntu 5.04 configuration.  However after a problem with Windows Update Windows 2000 takes for ever to boot up. So instead of trying to debug Win2k, I'd like to upgrade to XP (since my Athalon 900 MHz + 384 MB. Prob won't run Vista, from early reports. Not to mention that most Vista features are being moved to XP, too) I know that by Installing XP I'll whipe out the MBR.  What should I do to preserve/restore it so I can run XP and Ubuntu?[/QUOTE]

It shouldnt if you install from windows 2000. Insert the XP disk while win2000 is running and it should "upgrade" you to XP without touching your mbr

---

