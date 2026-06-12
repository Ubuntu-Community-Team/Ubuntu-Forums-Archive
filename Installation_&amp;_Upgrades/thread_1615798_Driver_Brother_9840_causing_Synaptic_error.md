---
title: "Driver Brother 9840 causing Synaptic error"
date: 2010-11-07
forum: Installation &amp; Upgrades
---

### Post by thomasmilo on 2010-11-07
I just used a Brothers script to install driver for my new printer MFC-9840cdw and now Synaptic will not open at all, giving following error message:
QUOTE
E: The package mfc9840cdwlpr needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.
END QUOTE

What can I do to get Synaptic to work again, because I read it is the best way to install these drivers.  I would like to uninstall the printer and start over using Synaptic.

I am running UBUNTU 10.10.

Thank you for any help.

---

### Post by Cheesehead on 2010-11-07
Your system is looking in /var/cache/apt/archives for a package named 'mfc9840cdwlpr' that was included with the Brother software.

If you locate it, and put a copy in /var/cache/apt/archives, then try Synaptic again.

---

### Post by Jose Catre-Vandis on 2010-11-07
So what did the script install? Perhaps you can post it here, and we can work out how to backtrack what it installed / did.

---

### Post by vandamme on 2010-12-10
Same problem here. I put the driver mfc9840cdwlpr in   /var/cache/apt/archives but still the same complaint, and now I can't  install or remove anything. I submitted a aptdaemon bug report....

---

### Post by vandamme on 2010-12-14
I WAS AN IDIOT.

The way to install printers is to let Ubuntu do it. 
[https://help.ubuntu.com/8.04/printing/C/printing.html](https://help.ubuntu.com/8.04/printing/C/printing.html)
It detects the printer, then goes and gets the right driver and downloads it. I didn't have to go to the Brother site and try to figure out which driver to get, then what to do with it. That's the MS Windoze way. 

Took 3 minutes. 

OK, that doesn't include installing a fresh Ubuntu  so I could get back to work after hosing my aptdaemon trying to install printer drivers.

---

