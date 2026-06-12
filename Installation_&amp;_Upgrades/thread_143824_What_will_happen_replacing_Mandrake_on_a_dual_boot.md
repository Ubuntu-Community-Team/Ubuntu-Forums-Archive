---
title: "What will happen replacing Mandrake on a dual boot"
date: 2006-03-13
forum: Installation &amp; Upgrades
---

### Post by lensisson on 2006-03-13
Hi, I'm new to Ubuntu and rusty on Unix/Linux having done some Unix system admin about 20 years ago. Needing to develop & test a web app on Linux/Unix with the intention of eventually setting up my own Linux server to run dyndns via my cable modem connection.
Have a dual-boot Win XP/Mandrake on the target machine now. Would like to replace Mandrake with Ubuntu. Mandrake installed GRUB 0.95 which is working fine. If I install the latest stable release of Ubuntu (5.10?) will it sort the boot stuff out or might I mess things up? This XP machine is my primary work machine and I can't afford to mess up XP. I plan to backup the XP partitions with Ghost to the second HD before doiing anything. I will probably backup the MBR just in case also, but I'm concerned about what might happen to Grub and my boot. Any help would be appreciated. Thanks.

---

### Post by patrick.ubuntu on 2006-03-15
Hi,
If my experience with leaving Mandrake for Slackware for Ubuntu with my dual boot is normal, the MBR will be overwritten with the new info of Ubuntu.  It should be fine, since it is basically rewritting the LILO just like it would the Windows bootloader with GRUB.
Hope this was helpful!
Cheers,
pt

---

