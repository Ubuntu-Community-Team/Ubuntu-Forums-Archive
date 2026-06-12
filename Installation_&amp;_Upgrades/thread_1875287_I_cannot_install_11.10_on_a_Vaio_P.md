---
title: "I cannot install 11.10 on a Vaio P"
date: 2011-11-04
forum: Installation &amp; Upgrades
---

### Post by gamx on 2011-11-04
Hi, 
I have created a USB disk to install Oneiric on my Vaio P. When it boots the splash screen works (except that it appears in text-mode), but the desktop (from where I should install the OS) never shows up. Instead, I get a blurry screen that indicates that it cannot get the screen resolution right. Any ideas?
Thanks,

Gamx

---

### Post by lightwarrior on 2011-11-04
Press F6 on the boot menu.
A list of options will come out.
Press ESC to go to edit the boot command line.
After --- add vga=771
or any VESA options listed here:
[http://en.wikipedia.org/wiki/VESA_BIOS_Extensions#Linux_video_mode_numbers](http://en.wikipedia.org/wiki/VESA_BIOS_Extensions#Linux_video_mode_numbers)

---

### Post by gamx on 2011-11-04
Thanks for the suggestion. I had already tried these options (vga=771 or xforcevesa, for example), but in that case I simply got the terminal, no graphical interface. I am not sure how to install ubuntu (or even if I should) from the terminal...

---

### Post by lightwarrior on 2011-11-04
Can you tell me which CPU and GPU you have?
Most probably very new ones.

With that info, perhaps there is a known bug or workaround.

---

### Post by gamx on 2011-11-04
The exact model is Sony Vaio P VGN-P70H. The processor is an Atom Z520.
By the way, in some forums I have read that the right option for my graphics card (the infamous gma500) is "poulsbo.asd=1 psb_gfx.asd=1". But that does not work either. It says that the option "poulsbo" is not recognized.

---

### Post by gamx on 2011-11-05
I solved the problem! I had to use the alternate installation disk/iso for Ubuntu 11.10. Installation worked just fine and after reboot everything is ok. Of course, the only problem is that I only have Unity-2D (and unfortunately I cannot run gnome-shell, which I like much more than Unity). So I guess I will have to install the emgd driver, which is not something I am looking forward to do, but...
Thanks a lot,

Gamx

---

