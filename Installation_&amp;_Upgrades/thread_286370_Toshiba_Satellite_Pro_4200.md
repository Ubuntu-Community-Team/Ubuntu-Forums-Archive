---
title: "Toshiba Satellite Pro 4200"
date: 2006-10-27
forum: Installation &amp; Upgrades
---

### Post by luistrigueiros on 2006-10-27
Hi,
I am trying to install Xubunto 6.10 on my old PIII Toshiba Satellite Pro 4200. 
I installed on it before DSL3.0.1 and had to use framebuffer with the option vga=791, to get X.
I tried several boot options, including the vga=0x318 video=vesafb 
but X is always starting in 800x600 mode. 
Could anyone please point me some directions.
Thanks, Luis

---

### Post by janga on 2006-10-27
I have an SP 4600 and the vga=791 option works just fine. Just being curious... did you add it to /boot/grub/menu.lst ? And what graphics card do you have?

---

### Post by luistrigueiros on 2006-10-27
> **janga said:**
> I have an SP 4600 and the vga=791 option works just fine. Just being curious... did you add it to /boot/grub/menu.lst ? And what graphics card do you have?

I haven´t edit the /boot/grub/menu.lst, I set the option by pressing F6 on boot. The graphics card is "Trident Blade3D" I belive that the following link is of someone that installed on RH6.2 on the same hardware [[http://www.arcetri.astro.it/lfini/LinuxLaptops/Toshiba.Sat.Pro.4200/#X11]](http://www.arcetri.astro.it/lfini/LinuxLaptops/Toshiba.Sat.Pro.4200/#X11])
Thanks, Luis

---

### Post by janga on 2006-10-28
Ok, in your other thread i saw, that you are using the LiveCD. So, what you could do is:
1. Boot the CD.
2. In Terminal, 
```
sudo dpkg-reconfigure xserver-xorg
```
and go through the wizard. If the "trident" driver isn´t working, try "vesa". When finished, press ctrl+alt+ backspace  to restart X.

---

### Post by luistrigueiros on 2006-10-28
Thanks a million janga. This has realy helfull, thanks to your previous post I was able to configure X and it working now for me.
I used the trident driver and keept all the defaults given by the wizard.
Cheers, Luis

---

### Post by Cuppa-Chino on 2007-08-11
having trouble booting 7.04 xubuntu live cd with toshiba 4600 any helpers what options to choose with the boot sequence ??

SOLVED - not enough memory to boot live cd

---

### Post by rustybronco on 2007-08-14
7.04 works fine out of the box on my 4200 pro 1024x768

---

