---
title: "Breezy - Printer Installation (Minolta Konica bizhub 162)"
date: 2007-02-27
forum: Installation &amp; Upgrades
---

### Post by mamza on 2007-02-27
I'm trying to install a Minolta Konica Bizhub 162 printer in Ubuntu Breezy, and I can't seem to find drivers for that printer anywhere. The printer setup dialog recognizes that the USB printer is connected but there're no Minolta Konica bizhub drivers in the choice of printers that follows. Has anyone had success installing that printer in Ubuntu, or what Generic printer drivers can I use?

Thnx,

---

### Post by freakalad on 2007-07-18
Hi there,

I have a BizHub 161f in the office, running off the network over port 9100.
I havn't had much sucess getting it to work under kubuntu/ubuntu as it should, and kanonical/minolta have not been very forthcoming with assistance.

I have found a resource that seems to do the job for me @
[http://256.com/gray/docs/misc/konica_bizhub_printer_cups_linux.html](http://256.com/gray/docs/misc/konica_bizhub_printer_cups_linux.html)

Device 	LPD/LPR Host or Printer
Device URI 	lpd://10.1.2.3/Print
Make 	Generic
Model 	Generic PCL 5c Printer Foomatic/hpijs (recommended) (en)

This has at least given me some rudamentary control, but still nowhere close to what is provided under w32; but at least it's a start

If I make any further progress, I'll let you know

-J

---

