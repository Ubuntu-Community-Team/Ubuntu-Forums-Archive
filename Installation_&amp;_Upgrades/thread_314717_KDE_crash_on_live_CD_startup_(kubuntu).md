---
title: "KDE crash on live CD startup (kubuntu)"
date: 2006-12-08
forum: Installation &amp; Upgrades
---

### Post by Sowe on 2006-12-08
When I try booting from a Kubuntu 6.10 DVD, towards the end of the boot process I get the message "The application KDesktop (kdesktop) crashed and caused the signal 6 (SIGABRT)". It still works after that, but without any desktop icons. I'm using the AMD64 ISO. The CPU is an Intel Core 2 Duo, motherboard is DFI Infinity 975X/G, nVidia video card. I also tried the SimplyMEPIS live CD (which uses KDE) and it works perfectly fine. The Ubuntu 6.10 live CD (with GNOME) boots fine too. I'd prefer to use KDE though. Any ideas as to what could be the problem? Thanks in advance.

---

### Post by Ub3r-L33ch on 2006-12-21
> **Sowe said:**
> When I try booting from a Kubuntu 6.10 DVD, towards the end of the boot process I get the message "The application KDesktop (kdesktop) crashed and caused the signal 6 (SIGABRT)". It still works after that, but without any desktop icons. I'm using the AMD64 ISO. The CPU is an Intel Core 2 Duo, motherboard is DFI Infinity 975X/G, nVidia video card. I also tried the SimplyMEPIS live CD (which uses KDE) and it works perfectly fine. The Ubuntu 6.10 live CD (with GNOME) boots fine too. I'd prefer to use KDE though. Any ideas as to what could be the problem? Thanks in advance.

Try adding this to the installer line:
noapic nolapic

I have the same problem as you and that gets it to the desktop with no problems.  I still am unable to install it though, it always freezes up.

---

