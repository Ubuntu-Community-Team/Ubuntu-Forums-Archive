---
title: "Does Hardware Detection Vary from the LiveCD to the Full Install?"
date: 2008-04-07
forum: Installation &amp; Upgrades
---

### Post by em4r1z on 2008-04-07
I recently bought a new laptop and I'm waiting for the 8.04 version to try Ubuntu again (I used the 6.x versions); in the meantime I've been trying various distributions and I'd like to know if the hardware detection from the LiveCD [usually] varies from that of the full install.

Let me elaborate, various LiveCD's I've tried (included those from Ubuntu a couple of years ago) will only boot if I set the "acpi=off" parameter, which makes the power saving features useless. Some others don't recognize my graphics card (nVidia GeForce Go 6100) properly and won't let me set the correct screen resolution (1280x800).

I'm a Linux starter and I'm not familiar with the drivers' installation yet, but having used Windows since it's 3.11 series I know how 'painful' it can be to find the proper drivers for your OS. I've downloaded various Linux drivers from the laptop and/or peripherics manufacturers, and I guess that once installed they should solve the hardware detection problems; but then there are some distributions, like Mandriva One 2008, which correctly detect every single part of my laptop by default.

Is it correct to 'judge' the hardware detection of a distribution based on its LiveCD version?

---

### Post by Belak on 2008-04-07
I don't think it's correct to judge hardware support based off of a live CD.

My reason for this is that your nVidia card should be supported with the restricted driver manager (System->Administration->Restricted Drivers Manager) just as mine was. Many hardware drivers are simple to install and many are included with Ubuntu as a default. Printer drivers, for example. There are an incredible number of printeres supported by Ubuntu without having to install anything extra (Unlike Windows)

Many drivers, you should be able to install with little hassle and you should be able to find info on many things by searching for (Specifically in the forums).

Cheers,
And Good Luck!

-Belak

---

### Post by em4r1z on 2008-04-09
Fortunately, Ubuntu 8.04 Beta for AMD64 nicely recognized all my devices when I tried it as a LiveCD. It had problems with my wireless connection and the suspend option, though, but I assume I can work that out once I install it or once the final version is released.

---

