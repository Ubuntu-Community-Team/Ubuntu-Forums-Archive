---
title: "Garbled display after Ubuntu upgrade to 2.6.32-* kernel"
date: 2011-02-04
forum: Installation &amp; Upgrades
---

### Post by MatthiasHess on 2011-02-04
[SIZE=2]I used Ubuntu 9 (Karmic Koala) for some time with no problems. When I  upgraded to Ubuntu 10 (Lucid Lynx) I ran into graphics issues.  After I  log in, the screen scrambles (a purple/green mess)--impossible to decipher  anything, although I can get out by marking the spot on the screen to  click for a restart, so Linux is working behind the scenes.  If I start  in recovery mode with basic graphics, I have no problems at all (other  than limited functionality).  If I start the old 2.6.31-22 kernel, I see  a bunch of "unmountable" errors in the startup script, but I can use  Linux normally with no apparent problems.  I'm running an IBM ThinkPad  A30 with ATI Mobility graphics.  Just to reiterate, the screen looks fine until I log in, at which point it goes bonkers. I've tried lowering the resolution, to no avail. I'm not running any proprietary drivers. What do I need  to change in order to fix this?[/SIZE]

---

### Post by mörgæs on 2011-02-04
Hi, welcome to the fora.

10.04 had problems with certain ATI cards. Best solution might be to try a live boot of 10.10 and a clean install, if the live boot behaves well.

---

### Post by MatthiasHess on 2011-02-10
Hi, and thanks.  The solution was actually a very simple update to the grub file, which I found in the release notes for 10.04.

> **Working around bugs in the new kernel video architecture**

Ubuntu 10.04 LTS enables the new kernel-mode-setting (KMS) technology by default on most common video chipsets. While this is a major step forward for the graphics architecture in Ubuntu, in some rare cases KMS will prevent your video output from working correctly, or from working at all. If you need to disable KMS, you can do so by booting with the nomodeset option. You can also save this setting so that it's applied at every boot by adding it to your grub config (for GRUB 2: edit /etc/default/grub and add nomodeset to GRUB_CMDLINE_LINUX, then run sudo update-grub; for GRUB 1: edit /boot/grub/menu.lst and add nomodeset to the line beginning with # kopt=, then run sudo update-grub).I'm not sure what KMS does, but it sure screwed up my display.  Adding the "nomodeset" boot command fixed everything!

---

