---
title: "Set a Default Boot OS when Dual-Booting W7/Linux?"
date: 2011-05-23
forum: Installation &amp; Upgrades
---

### Post by deevu on 2011-05-23
I am thinking about installing Ubuntu dualboot with Windows 7. However, I feel that it'd be a pain to select Windows 7 constantly as it is my main OS for work and school. Ubuntu would be for offtime tinkering and as such probably booted once or twice a week at most. I intend to use the system to use the OS not to use it for serious work. Before I install would it be possible to install it in Dualboot while maintaining the ability to boot W7 by default unless pressing a special key to come to the Grub bootloader or something like that.

sorry if it is too complicated,
DeeVu.

---

### Post by Hedgehog1 on 2011-05-23
I am in the same situation: My pc also has the printer on it, and when my wife needs to print she turns on the PC without powering up the display.

The way to change this so that Windows is on top of the menu is (after the install of Ubuntu is complete):

```
sudo mv /etc/grub.d/30_os-prober /etc/grub.d/09_os-prober
```

```
sudo update-grub
```

That makes grub (**GR**and **U**nified **B**oot loader) list your Windows install in the menu first, and the Ubuntu install after.


***The Hedge***

:KS

---

