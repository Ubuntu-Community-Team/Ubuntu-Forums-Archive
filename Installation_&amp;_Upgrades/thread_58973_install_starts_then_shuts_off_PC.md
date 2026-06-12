---
title: "install starts then shuts off PC"
date: 2005-08-22
forum: Installation &amp; Upgrades
---

### Post by tradeshares on 2005-08-22
Help
I have just tried to install hoary on my pc but is stops suddenly and turns my computer off within seconds of installation starting


I have to unplug power supply and plug back in to allow pc to restart.

This was also happening during Win XP install hence deciding to go hoary

PS I am new to linux but am able

---

### Post by glug101 on 2005-08-22
Hmmm.... I suspect a hardware problem since it is happening under two operating systems.  You might be able to confirm this by booting to a live cd and doing a physical check of your hard drive.  If this doesn't turn up anything, I'd try clearing the cmos on your motherboard through the jumpers. (this last step you'll have to check your motherboards documentation).

Good luck!

---

### Post by XoloX on 2005-08-22
Erm, doesn't removing the BIOS battery for a few minutes erase the CMOS aswell? Of course you'll need to unplug your pc while removing the battery, otherwise it won't help. Might be easier than using your mobo manual to find the jumper you need. Good luck.

---

### Post by glug101 on 2005-08-22
Yes, after awhile.  Removing the battery does reset the bios, but I've heard that it can take hours. (heard stories of between 8 and 16 depending on the motherboard)  15 min skimming the mobo manual is preferable ;)

---

### Post by tradeshares on 2005-08-22
thanks guys

Reset bios but still got problem

Going down path of testing everything.  Bios showing CPU operating temperature of 96 C so not a good thing to start with.

Will post back once hardware issue sorted out ](*,)

---

### Post by heimo on 2005-08-23
Sometimes I'm master at stating the obvious... But when was the last time you checked inside your computer, especially CPU heatsink and fan? At 96C it's obviously not working (or temp sensor is broken). If your BIOS is smart, it'll shut your computer down, otherwise you would have nice piece of smelling ex CPU, those things need ~1-2 seconds to fry without cooling.

---

### Post by tradeshares on 2005-08-24
[QUOTE=heimo]Sometimes I'm master at stating the obvious... But when was the last time you checked inside your computer, especially CPU heatsink and fan? At 96C it's obviously not working (or temp sensor is broken). If your BIOS is smart, it'll shut your computer down, otherwise you would have nice piece of smelling ex CPU, those things need ~1-2 seconds to fry without cooling.[/QUOTE]
 Thankyou heimo
"Sometimes I'm master at stating the obvious"
Sometimes we over look the simplest things. Something obviously failed in bios detecting temp.  It was reading 96 degrees at cold start. I thought maybe faulty thermal but it turns out fan and heatsink were not seated properly one side so yes 1 fried CPU later. Iam suprised it even started. It would still sit there and run for ages doing nothing.  Anyway problem solved and $300 plus bucks later we are on the road again.

All I need now is an answer with other post re bigpond login so I can set up hoary as internet gateway.

Thanks all for participation in this problem :)

---

