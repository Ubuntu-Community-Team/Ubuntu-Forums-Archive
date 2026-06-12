---
title: "installing 2nd video card cause boot to shell when restarting"
date: 2008-10-12
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by lime4x4 on 2008-10-12
I'm attempting to install a second pci-e nvidia video card. When i do and reboot the pc i get dropped to a shell prompt Any ideas?

---

### Post by jlacroix on 2008-10-13
> **lime4x4 said:**
> I'm attempting to install a second pci-e nvidia video card. When i do and reboot the pc i get dropped to a shell prompt Any ideas?

There is a bug with dual nvidia video cards that causes you to have to put the PCI:XX:YY:Z line in xorg.conf. I'm not 100% certain how to determine what to put for that line, but that is what your missing more than likely. It happened to me.

---

