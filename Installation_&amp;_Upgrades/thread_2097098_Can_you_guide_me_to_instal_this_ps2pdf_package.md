---
title: "Can you guide me to instal this ps2pdf package"
date: 2012-12-22
forum: Installation &amp; Upgrades
---

### Post by ofnirofnir on 2012-12-22
I have some .ps files that must be converted to .pdf, some googling leads me to a standalone installer package from: [http://manpages.ubuntu.com/manpages/intrepid/man1/ps2pdf.1.html](http://manpages.ubuntu.com/manpages/intrepid/man1/ps2pdf.1.html)
and now I have this file: "ps2pdf.1.gz" in my "download" folder. This file is as large as 1.2 kB (1,196 bytes) and I want to install this package.

Now what should I type in the terminal to install this ps2pdf package?
Thank You.

---

### Post by steeldriver on 2012-12-22
Not sure where you got the gz file from, but AFAIK the ps2pdf tools are scripts that use the ghostscript engine - if you don't have ghostscript I doubt they'll work. OTOH if you *do* have ghostscript, they should be installed as part of the package - which you can install via the Sotware Center / Synaptic / apt-get

---

