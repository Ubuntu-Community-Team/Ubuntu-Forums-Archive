---
title: "Upgrade from 10.04 to 10.10 not loading"
date: 2010-10-27
forum: Installation &amp; Upgrades
---

### Post by gewitty on 2010-10-27
I just completed an on-line upgrade from 10.04 to 10.10.

Everything went according to plan and the upgrade seemed to go without a hitch. However, when I rebooted following the finish of the process, the system would not start. After a short spell of disk activity, everything stopped and I was left staring at a blank screen - not even a blinking cursor in sight.

Fortunately, I had kept my original installation on a separate partition and this boots OK from the GRUB menu.

Has anyone else experienced this problem and does anyone know how I can sort it out?

---

### Post by Mark Phelps on 2010-10-27
YES, experienced something like this exact problem this last weekend when I did a routine upgrade of my existing 10.10 install.

Fixed it the following way:
1) Rebooted, and when GRUB came up, selected the Recovery option (second entry)
2) Got into a command line, where I entered "startx"
3) Got into the normal desktop, where I did a normal Shutdown
4) Rebooted the machine, selected the first GRUB option
5) Booted into a desktop OK this time.

---

### Post by gewitty on 2010-10-28
> **Mark Phelps said:**
> YES, experienced something like this exact problem this last weekend when I did a routine upgrade of my existing 10.10 install.

Fixed it the following way:
1) Rebooted, and when GRUB came up, selected the Recovery option (second entry)
2) Got into a command line, where I entered "startx"
3) Got into the normal desktop, where I did a normal Shutdown
4) Rebooted the machine, selected the first GRUB option
5) Booted into a desktop OK this time.

Thanks Mark. That worked.

---

