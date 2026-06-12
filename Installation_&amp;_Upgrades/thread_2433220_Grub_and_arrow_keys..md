---
title: "Grub and arrow keys."
date: 2019-12-15
forum: Installation &amp; Upgrades
---

### Post by wfp on 2019-12-15
When booting up, grub shows up just fine, but the arrow keys are not working so I can not move down, and boot into windows 10.

---

### Post by Bashing-om on 2019-12-15
wfp; Hey -

A thought: Bios passes to Grub it's layout.
Have you got a USB setting in that firmware that can be changed ? 

[INDENT][INDENT]maybe yes
[/INDENT][/INDENT]

---

### Post by yancek on 2019-12-16
For starters, did this ever work?  You have Ubuntu with Grub and windows and when you saw the Grub menu you saw both options and could select either, is this correct?  So what changed if this was the case?  If it never worked, that's a completely different situation.

Do you have an option in the BIOS on boot to boot from EFI file?  You can change the default boot in Grub files from UBuntu.  Does your keyboard work otherwise?

---

### Post by wfp on 2020-01-07
Thanks it was a USB setting. I have 2 USB 3.0 Ports in front, and two 2.0 Ports in back moved wireless keyboard setting from 3.0 to 2.0 that solved the issue now my arrow keys are working in grub, and I can now boot into windows thanks.

---

### Post by Bashing-om on 2020-01-07
wfp; Great !

Glad you got it fingered out :)

[INDENT]sometimes, it is easy
[/INDENT]

---

