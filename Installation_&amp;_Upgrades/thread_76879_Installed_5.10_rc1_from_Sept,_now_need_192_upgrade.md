---
title: "Installed 5.10 rc1 from Sept, now need 192 upgrades?"
date: 2005-10-15
forum: Installation &amp; Upgrades
---

### Post by dishbert on 2005-10-15
I downloaded the Breezy release candidate using the fast connection at work in  late September, burned the iso onto a CD, installed it a home, and it's been working great.

Today I did an apt-get update, and found that I need ***192 upgrades***, for 156 MB.  I only have dial-up at home, so this would be brutal.

How can I get the files I need?  If I get the formal 5.10 October release, could I upgrade from that CD if I change the sources.list?

---

### Post by adwait on 2005-10-15
yeah you could do that

---

### Post by dishbert on 2005-10-15
Good news.  I was hoping that would work.  Thanks for the reply 

So I'll wait until my official Breezy disc arrives, then just add a CDROM line to the sources.list. 

I should be able to find the exact wording somewhere, I know it was in the old default Hoary sources.list, but I didn't see it in the new one.  I'm guessing I'd comment out the other lines, to force the use of the CD.

Then I do an apt-get upgrade, and it loads from the CD?

---

### Post by dishbert on 2005-10-15
I think I just saw my questions answered a few threads down in this forum:

"just make sure that the breezy disk is included in /etc/apt/sources.list

i think sudo apt-cdrom add while the breezy disk is in the drive will add breezy to the list

then apt-get update and apt-get dist-upgrade and you should be fine. I upgraded from 5.04 to 5.10 without a problem"

That'll teach me to read more before I ask.

---

### Post by az on 2005-10-15
You can also just use synaptc to add your cdrom to the repositories.

It just does an
sudo apt-cdrom add
for you...

---

