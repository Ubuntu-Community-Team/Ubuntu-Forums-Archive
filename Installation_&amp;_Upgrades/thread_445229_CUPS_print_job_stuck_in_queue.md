---
title: "CUPS: print job stuck in queue"
date: 2007-05-15
forum: Installation &amp; Upgrades
---

### Post by happysnapper on 2007-05-15
Hi,

Just installed Kubuntu 7.04.

Have an Epson C64 connected to the parallel port.

At first CUPS didn't have the correct driver and so wouldn't install the printer.
Wasn't too sure which OSS drivers to download from linuxprinting.org so I went to Epsons site and followed the trail to get their drivers.

Everything appeared to install OK and applications can send their jobs to the queue.

The queue will write  PDF files with no problems (so the queue appears to be functioning)(PDF driver setup during install) but jobs for the Epson stay in the queue. The top job says it's printing, which of course it isn't.

The computer (Compaq AP550) is dual boot and the printer functions as expected under windows. I can therefore confirm that the physical link is OK, is switched on etc.

Any ideas on how I can free the queue jam up?

Nube at setting up printers on Linux and aptget system of doing things so any help would be appreciated.

Cheers

---

### Post by gwm on 2007-11-25
Hope this helps.

**Problem**
I upgraded to gutsy and now the first print job of the day gets stuck in the print queue, marked as pending. When I cancel the print job, it still hangs in there (even across reboots) but any further attempts to cancel the job generate an error.

**My Work Around**
Print a test page. This seems to clear things.
To print a test page I only know how to use the GUI interface:
**System > Administration > Printing > Select Printer > Settings Tab > Print Test Page**

HTH
:popcorn:

---

### Post by santito on 2008-04-15
Hi....

I am not an ubuntu user, but a debian lenny (testing) user, and i had the same problem....

The first job get printed, but stucked in queue. The following job wont ged printet until the first one is cancelled. Then the second job get printed, but also stucked in queue and so on...

I solved it in an indirect way.

In CUPS, i had setup the printer as ipp printer with an url like this:
ipp://192.168.25.222:631/printers/IPP_Epson_Printer

i have change "ipp printer" to "AppSocket/HP Jetdirect" and "ipp://192.168.25.222:631/printers/IPP_Epson_Printer" to "socket://192.168.25.222"

and now works perfectly!!!...

The printer is a Epson EPL-N2550

I hope this will be helpful as a workaround.

Regards

Santiago Castillo

---

