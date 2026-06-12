---
title: "upgrade to 18.04 LTS stalls at re-boot"
date: 2018-05-16
forum: Installation &amp; Upgrades
---

### Post by Robert_Stringer on 2018-05-16
Upgrade to 18.04 LTS OK till triggers re-boot then stalls and asking for LOGIN. Was not set up for login and cant get past this request?

Ubuntu 18.04 LTS robert-HP-255-G5-Notebook-PC tty1
robert-HP-255-G5-norebook-PC login:

---

### Post by Robert_Stringer on 2018-05-16
Correction

Ubuntu 18.04 LTS robert-HP-255-G5-Notebook-PC tty1
robert-HP-255-G5-Notebook-PC login:

---

### Post by dino99 on 2018-05-16
Probably some conflict with old settings/dependencies left behind after upgrading. Open a tty console to clean the system via 'gtkorphan' & 'bleachbit' (as root, carefully select options).
Also reconfigure gdm3 (now default) and purge lightdm if still installed.

---

### Post by Robert_Stringer on 2018-05-16
Thank you for the advice, unfortunately its gone over my head. Going to need a quite a bit of guidance/hand holding on this. Grateful for your analysis.

---

### Post by dino99 on 2018-05-16
open a tty console: ctrl+alt+F2
run 'startx'
install gtkorphan & bleachbit

if that fails, at least , run 'sudo apt-get autoremove'

---

### Post by Robert_Stringer on 2018-05-16
Thank you for the advice, unfortunately its gone over my head. Going to need a quite a bit of guidance/hand holding on this. Grateful for your analysis.

---

### Post by Robert_Stringer on 2018-05-16
Hi dino99.
Thanks. trying but as below
Ubuntu 18.04 LTS robert-HP-255-G5-Notebook-PC tty1
robert-HP-255-G5-Notebook-PC login:
Is already on screen with _ flashing and allowing me to input your ctrl+alt+F2
run 'startx' but not accepting or asking for password. tried to clear screen but unable.

---

