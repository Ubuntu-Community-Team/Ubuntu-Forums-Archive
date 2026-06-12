---
title: "Toshiba / Radion problems - solved step by step"
date: 2012-03-09
forum: Installation &amp; Upgrades
---

### Post by cc young on 2012-03-09
New Toshiba Satellite L745D-S4230 notebook with AMD A6-3420M processor and ATI AMD® Radeon™ HD 6520G graphics

when booting from CD screen goes black

hit escape in first screen, then used [FONT="Courier New"]nomodeset[/FONT] and able build system

screen black when rebooting, no Alt-Ctl-F1 etc available

booting, hit shift to get grub menu.  with "e" option, added [FONT="Courier New"]nomodeset[/FONT] to "liunx /boot/..."

booted.  F1 term available, no graphics in F7

per ati instructions:

  #enable canonical partners
  sudo vim /etc/apt/sources.list

  # remove fglrx (here not have been installed)
  sudo sh /usr/share/ati/fglrx-uninstall.sh
  sudo apt-get update
  sudo apt-get remove --purge fglrx*

  # install fglrx:
  sudo apt-get install fglrx
  sudo apt-get upgrade
  sudo reboot

graphics now work: KS

---

### Post by Das Goat on 2012-04-23
Could you elaborate a little bit? Where did you put these commands? Did you have to boot into the recovery console?):P

---

