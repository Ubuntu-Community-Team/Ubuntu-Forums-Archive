---
title: "Disabling Framebuffer in Installer"
date: 2010-07-12
forum: Installation &amp; Upgrades
---

### Post by snowsmash on 2010-07-12
I am trying to install Ubuntu 10.04 in text mode on a VIA EPIA-M motherboard with VT8623 VGA that gives a distorted screen when using the framebuffer. I used to be able to disable the framebuffer during installation by passing debian-installer/framebuffer=false to the kernel, and the screen would be fine. However, with Ubuntu 10.04, I still get a distorted screen even with debian-installer/framebuffer=false.

Any advice would be appreciated.

Youssef Eldakar
Bibliotheca Alexandrina

---

### Post by snowsmash on 2010-07-19
I tried video=vga16fb:off,viafb:off,vt8623fb:off. It still did not help.

Youssef Eldakar
Bibliotheca Alexandrina

---

### Post by JustinR on 2010-07-19
Just use the Ubuntu Alternate CD. Its all text based.

---

### Post by snowsmash on 2010-07-19
I am not installing from CD. I am installing using netboot.tar.gz. The installation is in text mode, but the framebuffer is apparently being used, which gives a broken screen, where the fonts and dialogs are distorted. I will check the ISOLINUX files on the alternate CD, though, and see if the kernel boot parameters have anything useful. That might be a good idea - thank you.

Youssef Eldakar
Bibliotheca Alexandrina

---

### Post by snowsmash on 2010-07-19
[https://bugs.launchpad.net/ubuntu/+source/module-init-tools/+bug/558569](https://bugs.launchpad.net/ubuntu/+source/module-init-tools/+bug/558569)

---

### Post by snowsmash on 2010-07-20
Was able to work around it!

vga16fb.modeset=0

Youssef Eldakar
Bibliotheca Alexandrina

---

### Post by hashstat on 2010-08-11
Thanks snowsmash. 'vga16fb.modeset=0' worked on my Dell Latitude D810 too.

---

### Post by chrishota on 2010-09-29
Also, this works for installing Ubuntu as a guest of Microsoft Hyper-V if the screen is sluggish to update.

We were seeing 7-10 second delays without putting this in as a kernel parameter in the install process—very annoying!

---

