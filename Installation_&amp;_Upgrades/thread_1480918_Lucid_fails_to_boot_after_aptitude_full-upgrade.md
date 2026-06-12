---
title: "Lucid fails to boot after aptitude full-upgrade"
date: 2010-05-12
forum: Installation &amp; Upgrades
---

### Post by gnopak on 2010-05-12
I run "aptitude update;aptitude full-upgrade" today, then I updated /etc/default/grub changing only the default boot line number, and I dully run update-grub, with no error messages. Now Kubuntu will not boot. The new kernel 2.6.32-22 is in the boot menu. When I turn the computer on, a blinking cursor appears on top line, column 8, and after a few seconds this cursor disappears and the screen is blank - my monitor indicates no video signal.

The failsafe 2.6.32-22 grub line does not boot either.

I tried pressing Ctrl-Alt-F1, Ctrl-Alt-F2 etc. up to Ctrl-Alt-F10 to get to a text mode login prompt, but the screen remains blank and my monitor indicates no video signal.

The workaround is to boot to kernel 2.6.32-21.

The machine is Athlon XP, 2GB RAM, ATI Radeon 9600

---

### Post by lemming465 on 2010-05-14
[Report the regression]("https://help.ubuntu.com/community/ReportingBugs") using ubuntu-bug and hope -23 fixes it?

---

