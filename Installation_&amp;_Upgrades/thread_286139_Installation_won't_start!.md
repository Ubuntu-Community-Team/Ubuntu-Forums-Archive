---
title: "Installation won't start!"
date: 2006-10-27
forum: Installation &amp; Upgrades
---

### Post by teme82 on 2006-10-27
Hi there!
I have weird problem. I donwloaded 6.10 amd64 installation cd-image and wrote it to cd-rw disc. Installation can't stat due to and x-server error. It says that it can't load driver for my gfx card. 
Now is this bug in the installer??

My Specs: Athlon64 3500+ 1024Mb ram 2 x 120 Gb HDD's and ATi X800GTO (R480 core)

---

### Post by penge on 2006-10-27
I have the same problem with Ati X800GT.

---

### Post by penge on 2006-10-27
Try this:

When you see error: Unable to start X server, follow these steps:
1. press Ctrl+Alt+F1 to bring up command line
2. write sudo nano /etc/X11/xorg.conf
3. find line "ati" and change it to "radeon"
4. press ctrl+x to exit. When prompted to save, press y
5. write startx

- GDM will start. :)

---

### Post by teme82 on 2006-10-27
> **penge said:**
> Try this:

When you see error: Unable to start X server, follow these steps:
1. press Ctrl+Alt+F1 to bring up command line
2. write sudo nano /etc/X11/xorg.conf
3. find line "ati" and change it to "radeon"
4. press ctrl+x to exit. When prompted to save, press y
5. write startx

- GDM will start. :)

Didn't work. ](*,)

---

