---
title: "please confirm a regression - not asked to save work on logoff"
date: 2008-09-29
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by zombiepig on 2008-09-29
I'm wondering if someone can confirm a possible regression in intrepid - with my copy of alpha 6+all updates, I'm no longer asked to save unsaved open work when I logout/restart/shutdown. For a while, in the early alphas, I got the new gnome dialog box listing applications with opened work, but now I get nothing and my computer happily shuts down and loses any unsaved work.

Can anyone confirm this for me? Just open text editor, type in a few characters, then try and logoff/restart/shutdown. Let me know if you get a prompt to save the work.

(bug report at [https://bugs.launchpad.net/bugs/276134](https://bugs.launchpad.net/bugs/276134))

---

### Post by bruce89 on 2008-09-29
Is this the shutdown one in the "System" menu, or the new menu in fast-user-switch-applet?

---

### Post by zombiepig on 2008-09-29
I don't get a prompt whichever way I shutdown..

---

### Post by rbmorse on 2008-09-29
I ***never*** saw a prompt when I shut down.

---

### Post by bruce89 on 2008-09-29
The same bug is filed upstream, I've linked it to the LP one.

---

### Post by zombiepig on 2008-09-29
I'm not sure that's the same bug - that upstream bug states that gedit is blocking logout, but not with a 'save' prompt. This is the behaviour I used to get with intrepid, but now I don't get any warning or prompts whatsoever, gnome just happily shuts down and loses the open work...

---

### Post by dbd on 2008-10-05
When I shutdown I'm finding that nothing auto saves. Amarok forgets any settings I've changed, liferea forgets what I've read etc...
If I want things to save correctly then I have to close all my apps before I shutdown. Do you think this is the same issue, or should I file a seperate bug? Are others suffering from this?
Also, intrepid is the first release I've used gnome rather than KDE, so perhaps gnome always did this, are they any longer term gnome users that can confirm gnome ubuntu used to let programs save what they were doing when shutting down?

---

### Post by aethralis on 2008-10-05
> **dbd said:**
> are they any longer term gnome users that can confirm gnome ubuntu used to let programs save what they were doing when shutting down?

Yes. In Hardy (gnome) this works like that. Have not tried this on Intrepid yet.

---

