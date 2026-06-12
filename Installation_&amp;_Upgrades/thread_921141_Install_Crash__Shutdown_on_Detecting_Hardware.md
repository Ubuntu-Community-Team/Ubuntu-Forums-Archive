---
title: "Install Crash / Shutdown on Detecting Hardware"
date: 2008-09-15
forum: Installation &amp; Upgrades
---

### Post by holybjork on 2008-09-15
Hello All,

I searched, but nothing came up in recent replies on the forums and Google proved to be useless.  I am having a problem installing Ubuntu, but I don't believe it to be related to the CD's as I also tried (blasphemy) Fedora and it shuts down at the same point.

Here are the symptoms - essentially I can get to the initial install screen (on both Ubuntu and Fedora) and get through the initial options (language, keyboard, etc).  It runs through the initial hardware detection, and then loads files from the CD.  Instantly after loading packages when it goes to check hardware again, the system shuts down.  It was rebooting until I changed the default power failure setting in the BIOS.

So far I have turned off Legacy USB support (which was stupid because that obviously disabled the USB keyboard I was using... :/), disabled multicore, disabled VT and XD, changed the hard drive setting from IDE back to ACHI and then back to IDE.  I ran a full three passes of MemTest86+ with no failures and it's a relatively new hard drive that tested good on the last test I did.  I also plugged the keyboard into the PS2 port and the same issue arises.  I fear that I may have an issue with the board or processor, but I was hoping that someone here might have an answer.

Here are the specs on my computer:
 - Intel DG965WH Desktop Board
 - Intel Core2 Duo E6300
 - WD 400GB SATA Hard Drive
 - 2GB of PNY Optima Memory

If there is a thread already discussing this, a link would be appreciated...

Thanks in advance,

Z

---

