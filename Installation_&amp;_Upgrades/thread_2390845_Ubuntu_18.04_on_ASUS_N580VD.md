---
title: "Ubuntu 18.04 on ASUS N580VD"
date: 2018-05-03
forum: Installation &amp; Upgrades
---

### Post by dario.luzzi on 2018-05-03
I'm trying to install Ubuntu 18.04 Desktop on two separate ASUS N580VD-DM028T ( Intel Core i7-7700HQ CPU,   Intel HM175 MB, GeForce GTX 1050)
Both of them show the same behaviour: after installation complete the system throws a lot of the following error and freezes:

```
BUG: soft lockup - CPU#7 stuck for 23s! [thermald:1349]
BUG: soft lockup - CPU#6 stuck for 22s! [kworker/6:2:240]
BUG: soft lockup - CPU#4 stuck for 22s! [kworker/4:6:3066]
```

the same happens running the live image.

is there some known issue with this laptop, or some relevant info I can check to look into the issue?

---

### Post by dino99 on 2018-05-03
As usual:
- check you run the latest bios/uefi version
- glance at output log via 'journalctl -b' 
- clean the system via 'gtkorphan' & bleachbit (as root, carefully select options)

---

### Post by art-akazantsev on 2018-05-13
when booting, hit ESC, go to GRUB menu (press E) , at the line with loading kernel (look for 'ro splash' etc), add 'acpi=off'  and / or 'noapic' (no quotes)  
Experiment with using both first.

---

### Post by art-akazantsev on 2018-05-14
When you manage to boot the system into GUI / shell, edit[FONT=lucida console] /etc/default/grub to add this (I removed 'splash' also)[/FONT]

GRUB_CMDLINE_LINUX_DEFAULT="acpi_osi=linux acpi_backlight=vendor"

[save]

>sudo update-grub
 
If your display stops working, install new nvidia drivers (you may need to boot once with 'nomodeset' option to disable GPU driver to pass through the lockup)

---

