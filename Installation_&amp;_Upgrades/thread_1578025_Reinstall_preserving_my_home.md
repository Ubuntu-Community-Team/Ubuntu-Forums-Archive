---
title: "Reinstall preserving my /home?"
date: 2010-09-19
forum: Installation &amp; Upgrades
---

### Post by damatta on 2010-09-19
I have two partitions: one for / and the other for /home ; now how do I reinstall ubuntu in the '/' partition so that I can reuse /home as it is?

Thanks

---

### Post by ronparent on 2010-09-19
After starting the install, when you get to step 4 of 7, pick the option to manually partition. In step 5 of 8, pick the partition the / in on and elect to format as /. Pick the partition with /home and elect to make it home but make sure it isn't checked for formating. Then on proceeding the / will be formated and all the files copied to it. The /home will be left alone except where updated files are needed and only those will be copied. When you reboot your system will be configured with a new / and have your old /home basically undisturbed. Some times you are left with some configuration problems which have to be cleared up but your data on /home will be undisturbed. Just make sure you select the same user name and password you are currently using. Only one user will be transferred into the new install.

---

### Post by srs5694 on 2010-09-19
Ronparent's outline is correct (as far as I know; I haven't checked the installation step numbers); however, it's always safest to back up before doing anything risky. I've seen posts from people who've claimed that their /home partition has been wiped clean even when following procedures like those described here. Of course, there's always the possibility of user error in such cases, even when the user swears up and down that there was none; but then again, there's always the possibility that *you* will make such a mistake, or that there's some bug that pops up very rarely and causes problems even when the user makes no mistake.

---

