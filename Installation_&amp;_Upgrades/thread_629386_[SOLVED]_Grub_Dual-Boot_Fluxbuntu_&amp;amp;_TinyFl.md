---
title: "[SOLVED] Grub Dual-Boot Fluxbuntu &amp;amp; TinyFlux problem has me beaten!"
date: 2007-12-02
forum: Installation &amp; Upgrades
---

### Post by Jose Catre-Vandis on 2007-12-02
Know a fair bit (well enough to get by) about grub but this one has me stumped.

I have an old laptop I am trying out light weight distros on which at present happen to be Fluxbuntu 7.10 and PCFluxbuntuOS (TinyFlux 1.0)

Fluxbuntu was installed first, boots fine. TinyFlux installed second, on a created partition. Grub installed onto partition to preserve the Fluxbuntu Grub. Following the Tiny Flux install I copied over the TinyFlux grub entries to the Fluxbuntu menu.lst. Then tried to reboot into TinyFlux and I got a kernel panic on loading of file system.

Tried reinstalling grub, same problem

Tried installing grub for TinyFlux. I could then boot to Tinyflux no problem but could not boot into Fluxbuntu - same problem kernel panic.

Tried all sorts of boot parameters but just get the same problem - kernel panic

Any pointers welcome :)

---

### Post by meierfra on 2007-12-02
Did try using "configfile".  Say tinyflux is on (hd0,2)

Then add this  to your Fluxbuntu "menu.lst":


title TinyFlux
configfile (hd0,2)/boot/grub/menu.lst


Selecting "TinyFlux" at the grub-men, will bring up the "TinyFlux" grub menu. If you use "timeout 1" and "hiddenmenu", You won't even notice the second  grub menu. The real advantage of this method is, that  you won't have to edit "menu.lst" after kernel updates.

---

### Post by Jose Catre-Vandis on 2007-12-02
Brilliant - that worked a treat, many thanks.

---

