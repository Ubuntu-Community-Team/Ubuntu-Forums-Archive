---
title: "cd rom mounting problem"
date: 2008-02-04
forum: Installation &amp; Upgrades
---

### Post by Niteowler on 2008-02-04
After trying live cd's or trying to install kubuntu, xubuntu, ubuntu (fiesty fawn), ubuntu 6.06, and ubuntu 7.10, I've came to the conclusion that my cd rom is not being mounted after receiving many freezes and errors.  What can I do to fix this?  I'm not quite sure sure what mounting means.  If it loads up to the install or to start the live cd screen, doesn't that mean it's mounted?  Have tried different cd roms,  bios settings, and changed cables to no avail.  Should I try and download a driver for the cd rom?  Aren't drivers stored on the hard drive?  My hard drive is blank.  Not exactly sure what to do or how to go about it.  Sorry for the long post and thanks for any responses.

---

### Post by Niteowler on 2008-02-04
Also try Ubuntu 7.10 alternate and it freezes.

---

### Post by kellemes on 2008-02-04
> **Niteowler said:**
> Also try Ubuntu 7.10 alternate and it freezes.

At what exact point it is freezing?

---

### Post by Niteowler on 2008-02-04
After the main screen while the orange bar is going across the screen.  It does this with all distros I've tried,  then after it sets there a while I get error listings.

---

### Post by Pumalite on 2008-02-04
Post exact error message.Hit 'Esc'

---

### Post by Niteowler on 2008-02-04
I was actually wrong.  Using the alternate cd, after I choose the language and keyboard selections, it goes to a blue screen with a white line at the bottom.  It just sits there with the cd rom running wide open.

---

### Post by Niteowler on 2008-02-04
Using Ubuntu 7.10 live cd, it freezes with the orange bar going across after the main screen.  Usually after I push a few keys on the keyboard it starts moving again then goes to black screen and then starts posting the following errors:
[134.288000] hdc:timeout waiting for dma
[139.388000] hdc:drive not ready for command
[201.216000] hdc:timeout waiting for dma
[206.264000] hdc:drive not ready for command
[268.108000] hdc:hdc:timeout waiting for dma

---

### Post by Pumalite on 2008-02-05
Go in the BIOS and set CD to different settings. In some boards 'Auto' will suffice. In others, AHCI, etc
In general terms Ubuntu is most comfortable when CD is 2nd Master.

---

