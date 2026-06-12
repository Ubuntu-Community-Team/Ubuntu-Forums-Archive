---
title: "Purple screen on boot from Wubi install needing &quot;ACPI workarounds&quot;"
date: 2011-12-13
forum: Installation &amp; Upgrades
---

### Post by yanom on 2011-12-13
So i used wubi to let friend try linux on new machine, which has a:

Nvidia GTX 570 graphics card
ASRock p67 extreme4 gen3 motherboard.

Installed wubi inside windows, then booted wubi for the first time.  it said "Press ESC now for additional options", and we had to press "ACPI workarounds" to get the installation to boot. after that finished and rebooted, if we select Ubuntu at the windows bootloader prompt, we get grub, and booting ubuntu from grub gives a blank purple screen and doesn't boot. So i need a way to get those ACPI workarounds back when booting up Ubuntu. I've tried:

pressing e at the grub menu to get boot options. I've tried typing in these following boot options (then pressing Cntrl-X to boot) but they don't work:
  acpi_osi="Linux"
  acpi_osi=
  acpi=off

so how do i boot?

---

### Post by yanom on 2011-12-13
_
bump

---

### Post by bcbc on 2011-12-13
Try nomodeset instead for the nvidia card and then install the nvidia drivers from "additional-drivers". (Make sure it's not an Optimus card (on demand GPU)). [http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

