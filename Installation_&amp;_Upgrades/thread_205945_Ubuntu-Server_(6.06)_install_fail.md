---
title: "Ubuntu-Server (6.06) install fail"
date: 2006-06-29
forum: Installation &amp; Upgrades
---

### Post by OliverSucher on 2006-06-29
When installing Ubuntu 6.06 I got following error when installing the base-system:
Debootstrap Warning
Warning: Failure tryinig to run: chroot / target dpkg --force-depends --install var/cache/apt/archieves/base-files_3.1.9ubunutu7_i386.deb var/cache/apt/archieves/base-passwd_3.5.11_i386.de

on the tty4 I got the following line ((wrote the last two lines)
June 29 10:43:56 base-installer: info: Running /usr/lib/base-installer.d/40netcfg
June 29 10:44:25 debootstrap: dpkg: syntax error: unknown user 'root' in statoverride file

as written above this happens during the baseinstall

ubuntu 5 was running fine on that machine....

anyway her the hardware description:
dual opteron
4 GB RAM
SATA- ICP-Vortex-Raid-Controller with about 6 HDs attached
hm, nothing special...
I switch off the delayed write funktion of the Raid-Controller during installation (this is always good for trouble)

ah, by the way, I also tried ubuntu 6.06 workstation it was also not working but I missed to write the detailed error-message

---

