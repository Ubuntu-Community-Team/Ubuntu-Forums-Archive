---
title: "[SOLVED] Black Screen Of Death - ubuntu 7.04"
date: 2007-08-25
forum: Installation &amp; Upgrades
---

### Post by wegoulet on 2007-08-25
:confused: 

I am using an 
ATI Radeon 7000 series PCI video card with 64Mb memory
AMD athlon 1600 cpu
1024 Mb ram
dual boot Windows XP SP2
ubuntu 7.04

Shortly after booting into ubuntu (whether I start a different application or not) ubuntu gives me a black screen. The only recourse I have is to perform a hard restart.

I have checked the AMD/ATI support site and it has no Linux drivers for my video card.

Any help with this problem would be appreciated.

Thanks in advance!

---

### Post by wegoulet on 2007-08-25
:confused: 

I am using an 
ATI Radeon 7000 series PCI video card with 64Mb memory
AMD athlon 1600 cpu
1024 Mb ram
dual boot Windows XP SP2
ubuntu 7.04

Shortly after booting into ubuntu (whether I start a different application or not) ubuntu gives me a black screen. The only recourse I have is to perform a hard restart.

I have checked the AMD/ATI support site and it has no Linux drivers for my video card.

Any help with this problem would be appreciated.

Thanks in advance!

---

### Post by Pumalite on 2007-08-25
At command line (Ctrl+Alt+F1): sudo dpkg-reconfigure xserver-xorg. Choose most defaults, choose 'vesa' as your driver. Then: startx

---

### Post by wegoulet on 2007-08-25
> **Pumalite said:**
> At command line (Ctrl+Alt+F1): sudo dpkg-reconfigure xserver-xorg. Choose most defaults, choose 'vesa' as your driver. Then: startx

You made a fatal error - you assumed that I already had xorg installed on my ubuntu system. It is not.

---

### Post by Pumalite on 2007-08-25
What's the 'fatality' of it?. Re-state your problem.

---

### Post by merlinus on 2007-08-25
You can manually edit /etc/X11/xorg.conf

```

sudo nano /etc/X11/xorg.conf

```

and change the driver to vesa, which might work in the absence of specific drivers for your video card.

-merlin

---

### Post by pgar23 on 2007-08-25
Check the "STICKY" on installing Ubuntu with ATI video cards...it may prove useful. It is located under the "ABSOLUTE BEGINNERS TALK" forum.

Good Luck

---

### Post by K.Mandla on 2007-08-25
I've merged your threads to keep all the relevant information in one spot. ;)

---

### Post by wegoulet on 2007-08-25
The video problem has been resovled.

After getting my ethernet connection working properly the update manager was able to download the 117 updates waiting in the cloud.

Those updates provided the necessary parts/pieces to correct the video

---

