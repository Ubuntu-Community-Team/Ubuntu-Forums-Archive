---
title: "Core2Duo AMD64 -&gt; black screen"
date: 2008-03-28
forum: Installation &amp; Upgrades
---

### Post by mock on 2008-03-28
Hi!
When i try the live cd of the 64 bit version i get a black screen. (my Graphic card is a 8800 GT).
Trying the 32 bit works, but i would really like to get the 64bit to function as i have a 4 GB memory (32 only shows 2 GB as does Vista). (bios get the extended mem to 4)
i have tried the ALT.ctrl F2 but it doesn't do anything.
I have tried to connect to it from another computer (as it responds to ping) but haven't found anyway that works.(telnet,ssh,vnc et.c.)
(worth noteing is that the 64bit works on my HP dv9000t  laptop (core2Duo))

---

### Post by .nedberg on 2008-03-28
You could try the alternate cd. It does not boot into the live system, but uses a text based installer. It is just as easy, but not as flashy.

---

### Post by PmDematagoda on 2008-03-28
You could also try booting the Live CD with parameters such as "nosplash" or "noapic".

When you reach the menu of the Live CD, press F6 then if you want to put "nosplash" as a booting parameter then just append "no" to "splash" and then try booting the Live CD.

---

### Post by mock on 2008-03-29
i Have used the umenu.exe (from within vista)
Is there a way to confugure the startup option there?

---

### Post by PmDematagoda on 2008-03-29
> **mock said:**
> i Have used the umenu.exe (from within vista)
Is there a way to confugure the startup option there?

I am not really sure about configuring the boot parameters through umenu, why don't you boot the PC using the Live CD? It's simpler than you may think it is:).

---

### Post by mock on 2008-04-04
It worked with  nosplash and noapic, but will that mean i will have no freq. scaling?

(and yes, now i can ultilize all my 4 gigs!)

---

### Post by tamoneya on 2008-04-04
I had a similar problem with 64 biit (Q6600, 8600 GTS).  I just walked away from it and it came up eventually.  The computer doesnt seem to be doing anything but it is just being slow.  It took me a while to figure it out.  How long have you been waiting?

---

### Post by mock on 2008-04-05
It took some time

mainly because it computer was REALY puzzeld when it didn't find a floppy drive.(i don't have one)
(it keept telling be that fd0 had some problem and i think that this is one of the problems)

(i don't know if it's a bug or if someone who know how should make a feature request for the installer (so it will check if a floppy drive exists)

---

