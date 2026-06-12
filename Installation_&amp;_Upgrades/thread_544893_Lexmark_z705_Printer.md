---
title: "Lexmark z705 Printer"
date: 2007-09-06
forum: Installation &amp; Upgrades
---

### Post by Robert Marley on 2007-09-06
Howdy,

I have a Lexmark z705 printer.  I set it up according to [This]("https://wiki.ubuntu.com/HardwareSupportComponentsPrinters/LexmarkZ705") wiki page.  It prints successfully.

The problem is, when I try to update, whether from the Update Manager GUI or using sudo apt-get upgrade, I get an error:
```
E: The package lexmark-z700-cups-driver needs to be reinstalled, but I can't find an archive for it.
```

Synaptic seems to pop up this same error sometimes when I start it.

I think the problem is that I installed the driver manually, like the wiki suggests, and that apt-get can't find the program in the repositories to update it.  Is there a blacklist i need to put the printer driver on?

Thanks for any help,
Robert Marley

---

