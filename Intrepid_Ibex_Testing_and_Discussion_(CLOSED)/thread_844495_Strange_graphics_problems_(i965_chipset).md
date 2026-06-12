---
title: "Strange graphics problems (i965 chipset)"
date: 2008-06-29
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by spamzilla on 2008-06-29
** Yes I know this is a developmental OS so don't take this as me moaning. I'm just finding out how the Intel 965 chipset is working for other people. **

Is anyone else testing Ibex using the Intel x3100 / 965 chipset? I'm having some odd problems.

Occasionally at bootup, the login page just won't appear, but the login sounds play. I can't switch to different terminal sessions either although you can see that the laptop is trying to change session. Restartign fixe the problem. I made no changes when I get this problem and this randomly happens.

Just now, compiz didn't startup, and I cannot select the Extra setting in Visual Effects and it doesn't want to to choose Normal, although eventually it gave in. Everything is a bit sluggish too. Only change I made here was install NM.

Every boot something behaves differently. Sometimes everything is really snappy and compiz is working fine. other bootups, either compiz is playing up or things are sluggish.

I'm hopeful that this graphics chip is going to be improved no end with GEM and the 2.4 drivers :)

---

### Post by bigdoby on 2008-06-30
sometimes happens to me too, like awn not showing or other little annoying problems.
Then i just open a terminal and write

compiz --replace &

and then everything is ok

---

### Post by ShirishAg75 on 2008-06-30
Hi all, 
 First of all there was an update to the intel driver yesterday. I also had issues and only with the help of recovery was able to fix things. I'm on Intel 845 chipset.

---

### Post by Nullack on 2008-06-30
The repoas have had a new compiz git dump so try it again :)

---

### Post by neatojones on 2008-06-30
> **ShirishAg75 said:**
> Hi all, 
 First of all there was an update to the intel driver yesterday. I also had issues and only with the help of recovery was able to fix things. I'm on Intel 845 chipset.

Did you ever get Compiz working with i845 chipset?  I never have gotten it to work.  Could you post your xorg.conf?

Edit:
Nevermind, I uninstalled it and then reinstalled it and it works now...

---

### Post by spamzilla on 2008-06-30
Yeah things seem better after installing the conmpiz updates.

---

