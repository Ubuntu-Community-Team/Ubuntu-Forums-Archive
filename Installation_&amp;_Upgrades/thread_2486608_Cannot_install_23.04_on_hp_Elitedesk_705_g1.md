---
title: "Cannot install 23.04 on hp Elitedesk 705 g1"
date: 2023-05-05
forum: Installation &amp; Upgrades
---

### Post by cigtoxdoc on 2023-05-05
Booting from same USB that has led to several successful installations.  Bootloader menu comes up, but when I try Ubuntu in normal or safe graphics, PC goes blank.  PC more than meets installation requirements and works in Win 10 64 pro.

John

---

### Post by MAFoElffen on 2023-05-07
Saw your last thread... You have nVidia right? At the Grub Boot, press the <E> key, arrow down to the line that starts with "linux"... <Arros-Right to where it says "quite splash". Remove the word "quite". After the word splash, add "nomodeset". Press <Cntrl><X> to boot.

---

### Post by cigtoxdoc on 2023-05-07
Thank you very much.  Device manager on the Elitedesk 705 g1 reports that the video is AMD Radeon HD 7480D.  John

---

### Post by MAFoElffen on 2023-05-07
Works with AMD Trinity graphics also. You could use either use the boot parameter or use "radeon.modeset=0"

---

