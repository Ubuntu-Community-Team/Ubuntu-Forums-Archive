---
title: "pixma MX330 printer not printing correctly on dell 960 SFF with 15.10"
date: 2015-12-27
forum: Installation &amp; Upgrades
---

### Post by darksidedude on 2015-12-27
good day all, I recently got my dad a "new" computer for Christmas. his old computer was running Ubuntu 12.04LTS the new computer I setup with 15.10 not thinking it would affect his printer. he has a Canon pixma MX330. it worked perfectly under 12.04 but in 15.10 it prints half of the page and stops for 3 minutes and finishes the print. to say thats unacceptable is an understatement! here is the interesting part though. I used my netbook running Ubuntu 16.04 plugged the printer into it for grins. it printed perfectly!

I get my usb with with 16.04 plug it into my dads computer, same problem as before. I really have no idea whats going on to be honest.

recap:
pixma MX330 works on old pentium 4 computer with ubuntu 12.04 x86, 
not on new Dell dimension 960 SFF with 15.10 or 16.04 x86 or x86_64 
works on HP mini 110 with 16.04 x86

driver in use: STP00668.PPD CUPS+gutenprint v5.2.11-pre1

---

### Post by ubfan1 on 2015-12-27
How much memory on the problem computer?  Could be a timeout, waiting for some sort of ACK.  Take a look at the protocols used on the printer.

---

### Post by matt_symes on 2015-12-27
I have changed the thread title for you to make it more specific to your problem.

---

### Post by darksidedude on 2015-12-27
thanks for the title change. sorry for being abstract.

the problem computer has 4.0 GB Ram and intel core 2 duo at 3.0Ghz

---

