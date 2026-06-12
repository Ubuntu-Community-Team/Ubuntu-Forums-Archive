---
title: "Problems installing Nvidia legacy drivers"
date: 2007-04-13
forum: Installation &amp; Upgrades
---

### Post by jordn on 2007-04-13
Hi there,

i am having a few problems installing the nvidia legacy drivers on my ubuntu system. i currently have an  NV5M64 [RIVA TNT2 Model 64/Model] which is definitely supported (under the legacy driver)

i used the command  **"sudo apt-get install nvidia-glx-legacy"**

after the install, it asked me to reboot the machine, which i did. however, upon reboot, there was no hardware acceleration present, and after attempting to run glxgears i received this error:

[B]Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't get an RGB, Double-buffered visual[/B]

i am quite unsure as to what the problem is, but i do remember that when i had a 6800XT, i had to edit the xorg file,

can anybody give me any pointers as to what to do next or, if i have to edit the xorg file, what to add?

thanks in advance,

jordn.

---

### Post by mikebai1990 on 2007-04-13
Are you using a laptop?

---

### Post by jordn on 2007-04-13
> **mikebai1990 said:**
> Are you using a laptop?

Nope, i am using a desktop.

Specs:

Pentium II Coppermine MMX @ 550Mhz (eek!)
320MB RAM 
20GB HDD
Nvidia RIVA TNT2 64

---

### Post by DJ Wings on 2007-04-13
This might help:
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)
It might still have legacy support. Hope I could be of help...

---

### Post by jordn on 2007-04-14
> **DJ Wings said:**
> This might help:
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)
It might still have legacy support. Hope I could be of help...

thankyou for your help. i tried to install the nvidia driver as instructed by the installer, but unfortunately it just caused me the same problems as installing it the manual way.

i just get the fatal error **no screens found** and get returned to the terminal.

any other suggestions?

---

### Post by bulldog on 2007-04-14
Did you perform the ```
sudo dpkg-reconfigure xserver-xorg
``` command?
In most cases this will help to reset the xorg.conf.

---

### Post by Swab on 2007-04-18
Same issue here, card is nVidia Corporation NV18 [GeForce4 MX 440 AGP 8x]

Any solutions?

---

