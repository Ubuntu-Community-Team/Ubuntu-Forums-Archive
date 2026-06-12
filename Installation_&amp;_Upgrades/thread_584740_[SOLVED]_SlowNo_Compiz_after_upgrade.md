---
title: "[SOLVED] Slow/No Compiz after upgrade"
date: 2007-10-21
forum: Installation &amp; Upgrades
---

### Post by Apocalypse_666 on 2007-10-21
Hi!
 I'm sorry to bother anyone if this question is already answered somewhere else, but I just couldn't find it. 
Here's the deal: Before I upgraded I had Compiz running fine and everything went smoothly. After I upgraded to 7.10 some things have been acting kinda weird. When I log in, I don't get the nice splash screen anymore, it just turns black and the cursor changes to a small cross. After a few seconds I get to my desktop, but the fancy Compiz eyecandy I had before are no longer there. Next to that, whenever I scroll along a document/webpage, it moves very slowly in a sort of stutterly fashion, as if it refreshes the page over and over... 
I tried removing compiz alltogether, but that didn't work. I have an ATI 9500 pro video card which I know isn't very good with Compiz/Xgl.  
My specs:
Pentium 4 2.4 ghz
512 mb RAM
ATI 9500 Pro videocard
Ubuntu 7.10

Any help will of course be VERY much appreciated!

Thanks,

Linus

EDIT: I just got Compiz running again, so that's good. However, everything is still VERY slow.

EDIT2: When running in Failsafe GNOME mode, everything runs smoothly, maybe that helps?

---

### Post by Stemp on 2007-10-21
Are you using xserver-xgl ? 
The free drivers (ati) ?

---

### Post by Apocalypse_666 on 2007-10-21
Yeah, I think so...

---

### Post by Stemp on 2007-10-21
Open Synaptic and check if xserver-xgl and fglrx are installed.

Is fglrx is not installed, you don't need xserver-xgl so remove it.

---

### Post by Apocalypse_666 on 2007-10-21
Okay! I think I did it! 
Here's what I did, in case anybody else has the same problem:
I installed the fglrx, and some related packages for configuring it, but I don't think these are important, and then I turned my restricted drivers back on, and voila! All I needed was the fglrx! Thanks man!

Linus

---

