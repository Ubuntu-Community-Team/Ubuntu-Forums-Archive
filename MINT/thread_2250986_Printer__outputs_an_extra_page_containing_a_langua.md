---
title: "Printer  outputs an extra page containing a language-specific header"
date: 2014-11-01
forum: MINT
---

### Post by monty2 on 2014-11-01
I am running Mint 17 and have a problem with my printer. The Mint forum has been no help so I am asking here.

I have a Lexmark Optra E312 printer connected to my computer via USB. This printer supports PostScript level 2, PCL 5e and PCL 6. I've used it with the PostScript driver in Fedora 16 but am having some problems with Mint17. CUPS is version 1.7.2.

If I use either the printer-specific driver or a generic PostScript driver, every print job begins with a page containing the text:


GPL Ghostscript 910 (ps2write)\n%%LanguageLevel: 2


(this is actual text on the page -- looks like a PostScript header to me, but shouldn't be printed). If I install the printer with a generic PCL driver, each print job begins with a page containing the following text:


L SET DENSITY=5
@PJL SET DUPLEX=OFF
@PJL SET BINDING=LONGEDGE
@PJL ENTER LANGUAGE=PCL


It looks as if CUPS is trying to send some commands to the printer that are physically printed on the page. Print output looks fine, I just get this extra page each time.

---

### Post by howefield on 2014-11-01
Thread moved to the "*MINT*" forum.

---

