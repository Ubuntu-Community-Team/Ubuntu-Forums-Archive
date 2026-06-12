---
title: "HELP - Unable to install 10.04 - nouveau error"
date: 2010-05-30
forum: Installation &amp; Upgrades
---

### Post by SeeJayDee on 2010-05-30
Hi All,
On friday I tried upgrading my kubuntu karmic to lucid. The upgrade failed for reasons I've forgotten... the upgrader said it had run 'dpkg --configure -a' or something, which I assumed meant that it was restoring the OS to a usable state... which it did not and now I have a broken distro.

TO THE POINT. I backed up my files and decided to do a CLEAN INSTALL of Lucid.

The Kubuntu installer GUI gets to the 'choose your keyboard layout' section and then freezes when you click 'next', shortly thereafter going to a black screen with infinitely scrolling messages of the form:

[ 1234.567890] [drm] nouveau 0000:02:00.0: Unhandled PMC INTR status bits 0x10000000

Ctrl-C does nothing... Every time I reboot and run the installer it does the same thing... any suggestions?

EDIT: I think the [1234.567890] is a timestamp of sorts, as it increases every second.

My system specs:
ASUS P5N-E SLI mobo
E6850 @ 3.60GHz
4Gb RAM
2 x GeForce 8800GTS 512 (SLI)
Kubuntu and GRUB are on 80Gb IDE drive (/dev/sdc1)

---

### Post by SeeJayDee on 2010-06-01
bump

anyone?

---

### Post by dabl on 2010-06-01
If you're sure the CD is a good one (md5sum checks correctly), then I would try pulling one of the Nvidia cards out of the PCI bus, and try the installer again. That's the only thing a little unusual about your hardware.  I don't know whether the Nouveau driver is able to cope with dual cards or not, but the Nvidia driver certainly is, and can be installed later, and then the second card can go back in and you can configure xorg.conf for dual cards.

---

### Post by skiani on 2010-08-10
Same problem with update and booting from 10.04 live CD. I just get a continuous stream of messages:

[FONT="Courier New"][1179.13123] [drm] noveau 0000:01:00.0: Unhandled PMC INTR status bits 0x10000000[/FONT]

---

