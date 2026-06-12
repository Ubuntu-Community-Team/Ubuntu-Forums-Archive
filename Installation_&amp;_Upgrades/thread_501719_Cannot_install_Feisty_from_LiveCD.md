---
title: "Cannot install Feisty from LiveCD"
date: 2007-07-15
forum: Installation &amp; Upgrades
---

### Post by Jored on 2007-07-15
New to Linux and Ubuntu. I've repeatedly tried the LiveCD installation and every time it fails at some point, takes hours from step 1 to 4 (never got beyond 4) and brings up different errors. The LiveCD is error free and worked fine on my other laptop. The problem is with my Dell Latitude LS400 (PIII 400Mhz, 256MB, 40GB HDD).

I've burnt an alternate CD and it boots a Caldera DR-DOS system which expects a prompt. Is this OK? What should I respond to the prompt to get into de Ubuntu installer to select text mode? 

:confused:

---

### Post by merlinus on 2007-07-15
Use the alternate install cd (you do not have enough RAM for a live cd install), but yours has defects, which is why it boots to a dos-type prompt.

Do the checksums for the .iso, and burn at no more than 4x.

Good luck!

-merlin

---

### Post by Jored on 2007-07-15
Thank you. I´ll reburn the alternate CD at lower speed and try again. However, the one I used passed  Nero's verification test. And the downloaded image passed the MD5Sum check.

---

### Post by Jose Catre-Vandis on 2007-07-15
I have also had trouble with installing Fiesty from the Alt CD on some machines. To overcome this i first install the "command line system" then once this is done, install ubuntu desktop:
```
sudo apt-get install ubuntu-desktop
```

---

