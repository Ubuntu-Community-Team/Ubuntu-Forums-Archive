---
title: "Dell Dimension 8400 - Problem with CD-ROM at installation phase"
date: 2005-02-13
forum: Installation &amp; Upgrades
---

### Post by hfoucher on 2005-02-13
I bought a brand new **Dell Dimension 8400** with the following configuration:
- Intel Pentium 4 530 HT (3.00GHz, 1Mo L2 cache, 800MHz FSB)
- 1 GByte of RAM
- HD 160 GBytes (SATA)
- DVD+R/+RW 16x/8x
- DVD ROM 16x 

I am booting Ubuntu installation CD ROM (official one, received by postal mail) on the DVD ROM 16x player.

After setting the language and the keyboard, it says it can't find the CD ROM whereas it just booted on it!!!

What  can I do? I tried every CD drivers proposed in the list with no success.
Is there a workarround for that or should I wait for a new realease to see that bug fixed? This installation CD ROM worked just fine with my previous computer.

Thanks.

---

### Post by orion_114 on 2005-02-13
Boot off the CD and when the promt comes up asking you to "press enter to install Ubuntu" press F1. Try using some of the options in there and see if that sorts it out. There is an option I think on the F5 page that says "For some Dell machines."

---

### Post by hfoucher on 2005-02-18
**Is still doesn't work.**
I pressed F1 then F6 and chose as proposed for "Certain DELL machines":
*linux aic7xxx=no_probe*<ENTER>

Installer still says: 
------------ [!] Detect and mount CD-ROM ------------
No common CD-ROM drive was detected.
[blabla]
Load CD-ROM drivers from a driver floppy?
<YES>   <NO>
----------------------------------------------------------------

Any other suggestion? I really want to install Ubuntu...

---

### Post by gump on 2005-02-18
You wil have to change a SATA setting in the bios.  I had the same problem with my Shuttle.  I have no idea where the setting would be in the Dell.  Mine was Integreted Peripherals.

---

### Post by hfoucher on 2005-02-27
What did you set in the Bios? Did you unset SATA? Did you set it again afterwards?

---

### Post by nobelis on 2005-02-27
I've exactly the same problem (and the same computer) and it's a known bug.
Check this : [https://bugzilla.ubuntu.com/show_bug.cgi?id=1440](https://bugzilla.ubuntu.com/show_bug.cgi?id=1440)

It seems that it's going to be resolved soon !
I've been waiting for 2 months ... :-\"

---

