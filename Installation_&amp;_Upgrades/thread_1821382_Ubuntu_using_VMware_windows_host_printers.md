---
title: "Ubuntu using VMware windows host printers"
date: 2011-08-09
forum: Installation &amp; Upgrades
---

### Post by pcarew on 2011-08-09
In particular, I needed to be able to print to my Windows "FinePrint" printer utility from UBuntu.
 
After much hunting, I have a configuration that allows Ubunto to print to all of the native Windows host printers (Real and Virtual printers)
 
Finally found a work around to accomplish this. A little involved to set up, but it does work.
 
I now have Ubuntu Linux running under VMware on a Windows 7 64bit Host.
I'm using the VMware virtual Printer support to write to a Windows Printer Port that is then redirected via Redmon+Ghostscript to FinePrint.
 
See:
Setting up VMware Guest image to use Windows host printers:
[http://www.vmware.com/pdf/ws7_manual.pdf](http://www.vmware.com/pdf/ws7_manual.pdf) - Page 180
 
Creating a Virtual Postscript Printer in Windows using Ghostscript and Redmon:
[http://www.stat.tamu.edu/~henrik/GSPSprinter/GSPSprinter.html](http://www.stat.tamu.edu/~henrik/GSPSprinter/GSPSprinter.html)
 
Also, for Win7 64 bit users, the 64 bit version of RedMon:
[http://www.winimage.com/misc/redmon/](http://www.winimage.com/misc/redmon/)
 
In Ubuntu, you will need to configure the printer driver for the Windows Postscript printer to match the PS Printer type chosen (e.g. HP Colour LaserJet 4500-PS)

---

