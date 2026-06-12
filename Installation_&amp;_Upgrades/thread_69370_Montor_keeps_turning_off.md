---
title: "Montor keeps turning off?"
date: 2005-09-26
forum: Installation &amp; Upgrades
---

### Post by steven22 on 2005-09-26
Hi,im new to this ubuntu os.I have been trying to install the ubuntu5.04 to my computer but when it has finished installing and try's to boot. My monitor keeps turning off.I have tryed all different settings but get the same outcome. Can any one help.:confused:

---

### Post by mlomker on 2005-09-26
Press escape when grub comes up and go into 'rescue' mode.  Press Control-D when prompted and get to a command prompt.  Type **dpkg-reconfigure xserver-xorg**.  Select 'vesa' as your video card and take the default options for everything else.

You'll want to figure out a better video driver to use once you are up and running.

---

### Post by steven22 on 2005-09-26
[QUOTE=mlomker]Press escape when grub comes up and go into 'rescue' mode.  Press Control-D when prompted and get to a command prompt.  Type **dpkg-reconfigure xserver-xorg**.  Select 'vesa' as your video card and take the default options for everything else.

You'll want to figure out a better video driver to use once you are up and running.[/QUOTE]

Thanks for your help mate will try.

---

