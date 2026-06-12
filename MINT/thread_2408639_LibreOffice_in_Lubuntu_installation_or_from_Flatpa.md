---
title: "LibreOffice in Lubuntu installation or from Flatpak"
date: 2018-12-20
forum: MINT
---

### Post by ubtnk on 2018-12-20
My computer is Compaq Presario V3000 Intel Core 2 Duo and 2 Gb RAM.
It's over 11 years old.
From May - July 2018, I used Linux Mint 19.0 xfce 32-bit and mainly LO Calc.
LO Calc crashed so often in every action, someone told me to uninstall LO which came with LM installation and install LO from Flatpak instead.
But I had not tried that yet.

So, I headed to Lubuntu 18.10 Desktop 32 bit since August 2018.
Working with LO Calc which came with Lubuntu installation, it is great.
LO Calc crashed only 1 time for my file is quite big and contains dozen of sheets.

Can you please tell me if I have to install LO from Flatpak?

---

### Post by ajgreeny on 2018-12-21
Simple answer; no!

I am assuming Mint does not use the flatpack version by default but we are a Ubuntu forum here so I could well be wrong about that; it does seem unlikely, but I suppose it's not impossible.

Command ```
dpkg -l libreoffice* | grep ii
``` will list all the libreoffice packages currently installed from the repos, and as far as I'm aware a flatpack version will show no output from that command so that will tell you which version you have.

---

### Post by ajgreeny on 2018-12-21
*Thread moved to **MINT**.* which is more appropriate and a better fit.

---

### Post by deadflowr on 2018-12-21
The Libreoffice flatpak page confuses me where it says
> Until LibreOffice 5.4.3, we also provided (x86-64&#8211;only) Flatpak builds directly through the TDF infrastructure (direct link to download old LibreOffice.flatpakref). 
From here: [https://www.libreoffice.org/download/flatpak/]("https://www.libreoffice.org/download/flatpak/")

The confusion is the state of **(x86-64 only)**, does that mean they only built 64-bit versions?
Or is the statement a tad too convoluted and just not an accurate picture of the LibreOffice flatpak status in general (meaning they do indeed built 32-bit versions as well)

Sorry if this causes even more, huh?, but it's something looking at the flatpak page that caught my eye.

---

