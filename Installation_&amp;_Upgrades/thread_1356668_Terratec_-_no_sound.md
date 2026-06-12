---
title: "Terratec - no sound"
date: 2009-12-16
forum: Installation &amp; Upgrades
---

### Post by leewin on 2009-12-16
Hi People.
I'm really stuck. This is my first attempt with linux (fed up with MS) I've installed Ubuntu 9.10 with absolutly no problems, except. I cannot get a single sound to be played. I've delved in head first ( I suffer from techno joy, no fear displayed when presented  with anything technical that I don't understand) I've played with everything but to no avail. My sound card is a Terratec Aurean 7.1 pci connected via coaxial cable. It definatly works, well does with windows on dual boot. I've also tried using a conventional cable.

Please help, I really want to run XBMC.

---

### Post by khelben1979 on 2009-12-16
Have you checked all the sound bars?

```
sudo apt-get install alsamixergui
```
Allows you to fix them if this is the source of the problem.

[ALSA SoundCard Matrix]("http://www.alsa-project.org/main/index.php/Matrix:Main") is a good place to start looking if there's a driver for your sound card.

---

