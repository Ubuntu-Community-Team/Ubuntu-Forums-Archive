---
title: "Does &quot;universe&quot; or &quot;multiverse&quot; interfere with dist-upgrade?"
date: 2005-03-31
forum: Installation &amp; Upgrades
---

### Post by Psquared on 2005-03-31
If I have these enabled in sources.list will they interfere with doing a dist-upgrade to Hoary? A related question is that could I have added stuff by having them enabled in Warty which would prevent or cause dist-upgrade to choke?

If so, is there any way to go back (downgrade) to a basic Warty installation?

---

### Post by fdoving on 2005-03-31
Give it a try.. if you use apt-get you can edit your sources.list and change all the warthys to hoarys.. and then do apt-get update and apt-get -s dist-upgrade.. the -s will simulate downloading and installing.. and then you'll find out if today is the day for dist-upgrading or not.

If today isn't the day.. and something breaks.. it's just a simulation anyway. So you'll just wait a day or two.. do a new apt-get update... and simulate again with apt-get -s dist-upgrade. If everything works OK in the simulation.. go for it!

Have fun with the power of apt-get :)

---

### Post by jdodson on 2005-03-31
[QUOTE=Psquared]If I have these enabled in sources.list will they interfere with doing a dist-upgrade to Hoary? A related question is that could I have added stuff by having them enabled in Warty which would prevent or cause dist-upgrade to choke?

If so, is there any way to go back (downgrade) to a basic Warty installation?[/QUOTE]

you should have no problems if your only sources are universe and multiverse.  

upgrade at ease.   :grin:

---

### Post by Psquared on 2005-03-31
OK, one last question. Will it make any difference if I do this from a Gnome session as opposed from the Linux shell without even X running?

Thanks in advance.

---

