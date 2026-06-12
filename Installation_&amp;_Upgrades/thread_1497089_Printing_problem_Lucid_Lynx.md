---
title: "Printing problem Lucid Lynx"
date: 2010-05-30
forum: Installation &amp; Upgrades
---

### Post by papahotel on 2010-05-30
I have upgraded to Lucid Lynx with just one problem. I cannot print on DL envelopes using may Epson PX710W. Was fine on 9.10. The preview page is corrupted. Could this be a CUPS problem requiring an update?

---

### Post by greenchilli on 2010-05-31
I'm having same issues since upgrading from 9.04. I install network printer (gestetner-DSc424) with the printing GUI - no problems. It picks up printer make+model and configures lpd Device URI. 

But no printing test page or any document. :confused:

---

### Post by greenchilli on 2010-06-02
On Ubuntu 10.04 the best way to setup network printer is with CUPS web interface. I could never print to this same network printer in the office before.
First you'll need the correct driver.
Locate the PPD driver file for printer - In my case Gestetner DCs424 driver (Search Google for drivers)

Point your browser to [http://localhost:631](http://localhost:631)  - For CUPS Interface

Go to the Administration/Printers section.

Then Add Printer - Choose "Internet Printing Protocol (http)" using socket URI e.g.  socket://158.155.40.243:9100

Describe the printer. Select "Share This Printer"

Then Provide a PPD File: choose the PPD driver file you saved on disk earlier (In my case it was a file named "Gestetner-DSc424-pxlcolor-Gestetner.ppd")

Add printer and you're done.

(You might have to tweak the printer settings using System/Administration/Printing GUI afterwards.  The default settings in my case was to print in color - I had to change it to Grey-scale because our company have disabled color printing on this particular printer)

It worked for me. :P

---

