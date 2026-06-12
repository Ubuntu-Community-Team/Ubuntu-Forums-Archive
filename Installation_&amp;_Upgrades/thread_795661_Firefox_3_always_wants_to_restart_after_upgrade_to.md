---
title: "Firefox 3 always wants to restart after upgrade to gutsy"
date: 2008-05-15
forum: Installation &amp; Upgrades
---

### Post by sphim on 2008-05-15
After upgrading from 7.10 to 8.04, firefox 3 works just fine.
However, none of the addons are enabled. When I go to the addons menu, the window says restart firefox to complete your changes. No matter how much firefox is restarted, the problem persists. I have Adblock Plus, NoScript, Fission, and Ubuntu Firefox extensions (Adblock is not compatible and is outright disabled).
Thanks in advance for the help.

---

### Post by Mhurst1 on 2008-05-15
It is happening becasue you are using firefox 3 and all of your addons are not compatible with it.

---

### Post by sphim on 2008-05-15
even so, shouldn't firefox not ask to restart continuously?
When adblock was incompatible, it just asked to disable the addon.

---

### Post by Prometheum on 2008-06-12
Shouldn't the title to this thread be "upgrade to hardy"?

I think I'm having the same problem. No matter how many times I restart firefox, when I go to Tools>Addons and any of the tabs in that window, it prompts me to restart. Addons that I've updated or installed won't take effect.

I think this might have something to do with my profile setup, as I have one profile for "secure" browsing that I use for paying bills and another for normal surfing. For instance, when I install an addon via apt, it will install to this profile and not to my default one (as marked in profiles.ini).

Is there a way to explicitly tell firefox it has restarted?

**_SUCCESS!_**

I was able to kick-start firefox into updating everything involved by moving ~/.mozilla/firefox/<profile>/extensions.rdf and restarting Firefox.

Hope this helps.

---

### Post by Palmyra on 2008-07-19
Prometheum, I am using Windows XP, but I had the exact same problem.  Renaming extensions.rdf solved the problem (instead of deleting/moving it, I just renamed the file -- extensionsOLD.rdf; this way, you can just change the name back if problems occurred).  

Now that I've done this, extensions are also behaving as they should.  For example, Zotero now displays its button again.

---

### Post by tr0k0l0 on 2008-11-11
Yes Prometheum !!!

It worked for me! , I moved "extensions.rdf" to "__extensions.rdf" and everithing worked right!

You should add [SOLVED] to the title of this thread...

---

### Post by excezzy on 2008-11-21
Erm, hallo. I've stumbled onto this forum by way of a Google search about the Firefox prollem.

I wonder if you could explain the solution in stupid-people terms?
>_<

---

