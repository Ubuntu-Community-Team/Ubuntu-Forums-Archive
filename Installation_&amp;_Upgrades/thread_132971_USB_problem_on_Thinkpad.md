---
title: "USB problem on Thinkpad"
date: 2006-02-19
forum: Installation &amp; Upgrades
---

### Post by evaristegalois on 2006-02-19
Dear all, Again, a total newcomer. My problem: I installed Ubuntu on my Thinkpad iSeries 1412 (about 7 years old) and it works just fine but my USB storage device doesn't work, and that's the only way I can conveniently transfer files onto my computer (no network card). The storage device is a Lexar MultiCard Reader RW023 with an SD card which works fine in Windows. Plugging it into my Ubuntu-converted Thinkpad yields no recognition and no sign of life on the card reader (the light does not come on). The USB controller is a USB 1.1 controller by ALi Corporation, product ID 0x5237. [COLOR=red]I'd love to have some help on this and make the switch from Windows to Ubuntu![/COLOR]
 evaristegalois
(Canada)

---

### Post by evaristegalois on 2006-02-19
Floppy doesn't work either. . . 

What do I have to do to make those things work?

evaristegalois

---

### Post by evaristegalois on 2006-02-19
btw, I installed using the ubuntu cd mailed to me

---

### Post by evaristegalois on 2006-12-16
the problem was that I disabled PnP OS in my BIOS -- a step which seemed to be necessary because my installation process would get stuck if I didn't do it. I solved that problem by writing ``linux acpi=off no acpi'' on the boot line before installing Ubuntu which took care of the installation problem. Then I forgot to enable PnP OS in my BIOS, almost gave up on Linux until a colleague pointed out the obvious to me. Re-enable PnP OS: everything's working fine now. Thanks.

---

