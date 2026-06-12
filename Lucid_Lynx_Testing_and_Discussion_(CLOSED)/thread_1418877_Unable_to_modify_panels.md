---
title: "Unable to modify panels"
date: 2010-03-01
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by phoogkamer on 2010-03-01
I am running lucid alpha 3. Upgraded from karmic and cannot adjust my panels anymore. Is this a known issue? When right clicking the panel I only get "Help" and "Panel Info" options.

Thx

---

### Post by dave1403 on 2010-03-01
Hi mate,
I had a similar problem. Are you using the netbook version? because if so, then the panels are locked by default!
There is a way to get the panels unlocked in the Netbook Edition. Look here:
[https://help.ubuntu.com/community/UbuntuNetbookEdition/ConvertGnomeSession](https://help.ubuntu.com/community/UbuntuNetbookEdition/ConvertGnomeSession)
If you aren't using netbook version then I can't really help you :S

---

### Post by phoogkamer on 2010-03-01
Thanx for the tip, but I don't use UNE. I am on a normal desktop version. Maybe you're suggestion leads me to the place in gconf where I can find something usefull to solve my issue.

---

### Post by phoogkamer on 2010-03-04
Here I am adding a screenshot to this post to clarify my issue.

---

### Post by Atermoon on 2010-03-04
Open gconf-editor and navigato to apps > panel > global. Uncheck the "locked down" checkbox and you're done.

---

### Post by phoogkamer on 2010-03-04
Yes, thx. That's it.

Problem solved.

---

