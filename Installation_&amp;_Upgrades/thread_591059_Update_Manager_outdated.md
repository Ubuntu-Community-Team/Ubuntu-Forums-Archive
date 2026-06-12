---
title: "Update Manager outdated?"
date: 2007-10-25
forum: Installation &amp; Upgrades
---

### Post by interse on 2007-10-25
I have used Update Manager to check my laptop for updates.  While my desktop Update Manager shows  Update for 7.10 Available,  the Update Manager on my laptop returns only the message that my computer is up to date, even when I activate Check.

Is there something I can do to get Update Manager to indicate that 7.10 is available?  I have 7.04 installed.

---

### Post by seldenthuis on 2007-10-25
Try this:
```
sudo update-manager -c
```

---

### Post by interse on 2007-10-25
Tried,  'sudo update-manager -c '  several times.  Still the same Update Manager message,
You system is up to date.   No alert to the Upgrade to 7.10

---

### Post by seldenthuis on 2007-10-26
What happens if you select a different server in System->Administration->Software Sources and run 'sudo update-manager -c' again?

---

### Post by Bleak Outlook on 2007-10-26
its a sad fact that both your comps have decided to gang up on you and freak you out by acting different 
it happens 
try explaining that you know their game and you wont stand for it

---

