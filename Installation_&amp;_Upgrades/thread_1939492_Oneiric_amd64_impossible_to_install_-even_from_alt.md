---
title: "Oneiric amd64 impossible to install -even from alternate CD"
date: 2012-03-11
forum: Installation &amp; Upgrades
---

### Post by todoporron on 2012-03-11
Hello folks.

A couple of days ago I bought a new desktop PC and since then, I've been trying to install oneiric (64 bit) on it with absolutely no good results. I´ve searched so far with no good resuts.

At first, I tried the live desktop CD which kept freezing just after starting loading Ubuntu no matter which options I chose. I suspect this has something to do with the graphics card (It happened on my old pc every time I installed Ubuntu). I know there's always the alternate CD, which I downloaded after many failed install attempts.

There beguins my nightmare. The installation process with alternate CD goes perfectly well but when finishing the step called "program selection and installation" ("Seleccionar e instalar programas" in my locale), comes out a message stating that there was an error during that step, taking me after to a menu of all the steps of the installation process. No matter which step I chose, I get nothing but the same message error on that step.

I checked the MD5SUM of the ISO file and its ok. I also checked the CD for defects and its also Ok. Also did a memory check and its OK.

I tried several times with onbard graphics on/off and PCI graphics card on/off but I get always the same error. I also tried USB desktop install.

Any Clue will be more than welcome.

My PC configuration is as follows:
AMD Phenom II X6 1045T
Board: Gigabyte 78LMT-s2p
HD: 1TB SATA
Memory: 8 gb (2x4GB kingston pc3)
Graphics: GeForce GTX 550 TI (PCI)

Thaks for your help

---

### Post by todoporron on 2012-03-13
Murphy's law:

Never tried the "nomodeset" option, I did it and, voilá....Now I'm posting from oneiric.

---

