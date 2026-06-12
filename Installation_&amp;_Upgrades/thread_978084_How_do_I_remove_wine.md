---
title: "How do I remove wine?"
date: 2008-11-10
forum: Installation &amp; Upgrades
---

### Post by Nucleric on 2008-11-10
Hi. I'm new to Ubuntu and Linux in general. I I would like to know how to i remove wine. I've tried the Synaptic Package Manager and I've tried the command posted  [COLOR="Red"]sudo apt-get remove --purge wine[/COLOR] on the Ubuntu forum by another user and still not working. Any help would be highly appreciated Thank You.

---

### Post by VitalBodies on 2008-11-10
> **Nucleric said:**
> Hi. I'm new to Ubuntu and Linux in general. I I would like to know how to i remove wine. I've tried the Synaptic Package Manager and I've tried the command posted  [COLOR="Red"]sudo apt-get remove --purge wine[/COLOR] on the Ubuntu forum by another user and still not working. Any help would be highly appreciated Thank You.

Try this:
Applications > Add/Remove... > Show: All Open Source Applications > Search "wine". 
Then just remove the check mark and click the APPLY CHANGES BUTTON.

---

### Post by flameproof on 2008-11-10
> **VitalBodies said:**
> Try this:
Applications > Add/Remove... > Show: All Open Source Applications > Search "wine". 
Then just remove the check mark and click the APPLY CHANGES BUTTON.

When I do that I get:

> E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

PS: I get the same when I type [COLOR="Red"]sudo apt-get remove --purge wine[/COLOR] in Terminal.

---

### Post by oldos2er on 2008-11-10
In a terminal run "sudo dpkg --configure -a"

---

### Post by tvtech on 2008-11-10
> **oldos2er said:**
> In a terminal run "sudo dpkg --configure -a"

seriously some one needs to make a tut on this , or file it as a bug, or just add it as an auto script somewhere that it just does this everytime this error pops up, I can't even begin to tell you how many times I've seen this come up.   seriously it's amazing.  p.s. if this gets solved don't forget to mark your thread as solved.

---

### Post by flameproof on 2008-11-10
> **oldos2er said:**
> In a terminal run "[COLOR="Red"]sudo dpkg --configure -a[/COLOR]"

I did that. Then I wanted to unclick: [COLOR="Red"]Applications > Add/Remove... > Show: All Open Source Applications > ..wine..
[/COLOR]

I got an error that pointed me to manually remove the dependencies in the Synaptic Package Manager. So I opened it and typed "Wine". 4 "hits" came up, 2 of those were installed. I removed those 2. 

After that Wine was gone from "Applications".

The software that I wanted to install, and triggered that error in the first place, installed now.

Conclusion: Wine seem to bring limitations to Ubuntu. If possible avoid it.

My problem is solved.

---

