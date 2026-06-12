---
title: "Feisty - Black screen on install"
date: 2007-04-15
forum: Installation &amp; Upgrades
---

### Post by Tourney3p0 on 2007-04-15
There may be a couple different issues here.

First off, think about how when Ubuntu initially boots from the CD, you're given a boot list to select which method of startup/installation you'd like.  You can hit enter to boot, or wait a few seconds and it will boot from the default entry.  I do not get this part.  Literally as soon as it attempts to boot from the CD, I immediately get the "Loading isolinux.." message. 

When this happens, it goes to a black screen afterward.  I'm using an ATI card with DVI out, so I was thinking I could just install it via text mode.  However the above problem means that I can't even do that.

While I have the black screen, I can hear the CD cycling.  If I wait for awhile, I'll finally get what looks like the Gnome startup screen, but once it gets here the computer will freeze.  

I tried using 6.10 and I get the similar no bootlist/black screen problem, but it never makes it to anything beyond a black screen.  Both CD's work fine in another computer.

Any ideas?

---

### Post by zvacet on 2007-04-15
When it  start to boot press F1.It is help.

---

### Post by Tourney3p0 on 2007-04-15
I think you've misunderstood what I'm saying.

Yes, it SHOULD be help.  But my problem is the computer completely skips that part.  There is no chance to hit F1.

---

### Post by Tourney3p0 on 2007-04-15
I've found the problem.  Everything works great when I use VGA instead of DVI.  I actually had to borrow a VGA monitor to test this.  So basically something is broken with Ubuntu's installer and DVI.

---

### Post by stevecs on 2007-04-18
What type of monitor/resolution do you have?   I've had a similar black screen problem w/ my HP LP3065 (30" LCD) which requires dual-link dvi.   I put a bug ticket in for it but don't think it will be fixed in 7.04.

---

