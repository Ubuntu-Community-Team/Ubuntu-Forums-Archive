---
title: "Sound on Via EPIA MII (C3 1200 Nehemiah)"
date: 2005-03-06
forum: Installation &amp; Upgrades
---

### Post by ubnik on 2005-03-06
I'm having trouble getting sound working on this newish mini-itx board from Via.  Via have rather half-heartedly released an rpm binary driver, but it seems to only work on 2.4 kernels.

Has anyone managed to get sound working properly using the via82xx alsa driver with a 2.6 kernel (with either warty or hoary)?  Mine suffers from an endless loop of a about half a second of the ubuntu gdm login .wav (a process called "aplay" needs to be killed before I can log in, and then esd gets stuck on a loop of the logging in wav).

Any tips would be appreciated.  I'm not particularly keen on trying the 2.4 kernel with the binary drivers, but if anyone else has done that I'd be happy to hear from them too.

[It would be nice if via had just made good on their linux-friendly rhetoric and released some source for their drivers.  They've only got a 2.4 kernel binary driver.  I'd certainly recommend against buying an M series EPIA board for use all of its features with Linux/Ubuntu]

---

