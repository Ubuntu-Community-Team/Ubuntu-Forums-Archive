---
title: "Really quick question about installing with a GeForce 8500"
date: 2008-01-02
forum: Installation &amp; Upgrades
---

### Post by Arken on 2008-01-02
I just purchased a new PC, and I want to install ubuntu. I do not have an integrated card, and my graphics are being outputted via. S-video. Will I need to install Ubuntu in Safe Graphics mode, then get the driver for a GeForce 8500? Or will it work via. normal mode?

---

### Post by Sef on 2008-01-02
> I just purchased a new PC, and I want to install ubuntu. I do not have an integrated card, and my graphics are being outputted via. S-video. Will I need to install Ubuntu in Safe Graphics mode, then get the driver for a GeForce 8500? Or will it work via. normal mode?

Via normal mode.  Ubuntu should install some nonrestricted drivers with no problem.  If you want to install the restricted drivers - needed for Compiz-Fusion- just go to System > Administration > Restricted Drivers Management.

---

### Post by ~LoKe on 2008-01-02
Yeah, it'll work just fine.  It'll be using the "nv" driver.  Install and enjoy! (I don't even have onboard graphics and I used my 8600GT).

---

### Post by Arken on 2008-01-02
Alright, I'll try it, right after I get this goshdang heatsink in =D

---

### Post by Arken on 2008-01-03
Alright. I'm trying to install it (Kubuntu 7.10 64 Bit AMD) and every time it goes into a "no input mode" on my monitor. What does this mean? I'm going to try it in safe graphics while I download the Ubuntu 7.10 iso instead of kubuntu.

---

### Post by oltranzista on 2008-01-17
I have an Nvidia GeForce 8500GT 256 card and it did not work with Ubuntu's install cd (at least for me it didn't), safe graphics mode or not. You may need to get the "alternative" install iso to do it.

I have installed openSUSE 10.3 in normal graphics mode and it worked, then you can get the more specific driver installed for it using openSUSE's "one-click" install function.

I have also installed Sabayon with this card also, this was using their text install mode.

Both openSUSE and Sabayon displayed alerts about "3D not enabled, only 2D" whatever that means.

I have NOT been able to get the SVIDEO output to work yet. If anyone figures this out please pm me. :)

---

