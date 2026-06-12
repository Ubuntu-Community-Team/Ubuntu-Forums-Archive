---
title: "no display"
date: 2008-04-13
forum: Installation &amp; Upgrades
---

### Post by norman_069 on 2008-04-13
Hello

I have an intel motherboard, dual 2 cpu and an 8800 gt graphics card. I installed windows xp on my first sata drive no problem.  Then i went to install debian on the other drive and everything worked ok except it would not start up in x, it said that there was no "monitor" or "screen" recognized.  Then I tried ubuntuy and the same thing happened.  Can some one please help me with this.  Thanks

---

### Post by Pumalite on 2008-04-13
Install with the Alternate CD and configure your xserver at the end of the installation.

---

### Post by norman_069 on 2008-04-13
I don't think i realy know how to do thabut i am going to give it a shot right now.

---

### Post by norman_069 on 2008-04-13
ok, I got it installed with the alt. cd but now it is running in low graphics mode.  What should i don next to get it working like normal.  Thanks

---

### Post by Pumalite on 2008-04-13
sudo dpkg-reconfigure xserver-xorg
Accept most defaults, choose vesa as the driver
Once in the system install appropriate driver (-169.12-)

---

### Post by norman_069 on 2008-04-14
got it working with envy

Thanks

---

