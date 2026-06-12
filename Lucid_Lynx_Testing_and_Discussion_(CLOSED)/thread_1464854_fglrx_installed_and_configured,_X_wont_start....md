---
title: "fglrx installed and configured, X wont start..."
date: 2010-04-28
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Dilutu on 2010-04-28
Hi 
I purged fglrx folowing posts in this forum .Then, I  did "sudo apt-get install fglrx && sudo aticonfig --initial". Everything seemed fine but then when I reboot, I only get "low graphics mode". Checking my xorg log file, this is what I have:
"[    15.654] [atiddxSetup] X version mismatch - detected X.org 7.1.0.0, required X.org 7.5.1.0
[    15.654] (II) UnloadModule: "fglrx"
[    15.654] (II) Unloading /usr/lib/xorg/extra-modules/modules/drivers/fglrx_drv.so
[    15.654] (EE) Failed to load module "fglrx" (module requirement mismatch, 0)"
My card is a Radeon HD 2600 PRO AGP. Last week, it worked good with fglrx but some upgrade broke it....

---

### Post by BrokeMahPC on 2010-04-28
Try this guide for removing drivers:
[https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver](https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver)

I would not install it like that - enable it in from System-Admin-Hardware Drivers
Guide here
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

I always give it a sudo aticonfig --initial -f
If you have problems with crashes and instability try:
radeon.modeset=0
in the grub boot string. That will disable KMS - the fglrx does not work with it.

Be aware that if you use the current fglrx you will get a nasty plymouth splash screen. Is the default radeon driver not working for you? If it is - stick with that.

---

### Post by Dilutu on 2010-04-28
Thanks but I followed those links for my remove reinstall allready.The default radeon driver worked good for me, but flash fullscreen worked better (almost no tearing) with fglrx.I will try with "radeon.modeset=0"                                                                                         
Th.

---

### Post by clhsharky on 2010-04-28
HI Dilutu

Installing fglrx drivers on Lucid and your Radeon HD 2600 PRO AGP card will only work with cat 10.04. It just came out today or the one in repos like BrokeMahPC suggested. If you manually install from ATI it will all ways break with kernel upgrade. AGP cards can be problem. 

Sharky

Radeon with xv enabled is already tear free.

---

### Post by Dilutu on 2010-04-28
Ok, booted with "radeon.modeset=0" but still no go for fglrx. I still get the same error in xorg log telling me that "X version mismatch - detected X.org 7.1.0.0, required X.org 7.5.1.0"...
I did not try with the latest fglrx from ati, only from jockey and then from synaptic.Radeon with xv is ok with youtube, but I get some trouble with sites like "tou.tv" (French canadian tv site)

---

### Post by clhsharky on 2010-04-28
HI 


Looks like a upgrade left wrong xorg.

Sharky

---

### Post by Dilutu on 2010-04-28
Synaptic tells me I have version 7.5.1 xorg....

---

### Post by djchandler on 2010-04-29
The Lucid repository has the latest fglrx ATI driver, 8.723, which is the driver currently packaged in the Catalyst 10.4 download just released April 28, 2010 by ATI/AMD.

I installed fglrx with Jockey on a fresh Release Candidate iso installation and all is just fine. AFAIK there's now no need to install by the method you described in your first post. As recently as the Beta 1 there were problems, but not since the Beta 2 freeze. I'm running the same generation of GPUs on two of my machines (Radeon 3100 IGP, HD3450 discrete card).

---

### Post by Dilutu on 2010-04-29
Well, removed every thing fglrx (again) and tried Jockey and this time, it worked !
Thank you all for your inputs. Th

---

