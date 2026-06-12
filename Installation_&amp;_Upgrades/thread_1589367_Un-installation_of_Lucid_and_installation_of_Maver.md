---
title: "Un-installation of Lucid and installation of Maverick."
date: 2010-10-06
forum: Installation &amp; Upgrades
---

### Post by Mr_VeRiTy on 2010-10-06
Hi, When I had karmic I tried upgrading to lucid via the update manager, the upgrade went fine, but it didn't install everything it was supposed to, and the system was really slow, so I completely un-installed lucid and did a fresh install of Lucid and everything was fine. Now that maverick is on the way, I'm not sure I want to use upgrade manager to upgrade.

So my question is; How can I do a fresh installation of maverick without losing my music an videos, I don't mind about losing my programs,  but I have no means of backing up everything else. I have a separate / partition and /home partition so I was thinking I could delete my / partition while leaving my /home (and thus my stuff) intact, would this work?

---

### Post by Rubi1200 on 2010-10-06
The perfect setup for a fresh install!

Delete the Lucid / partition, leaving /home untouched and then install Maverick into the free partition choosing to install / there.

You keep your /home with all your data and get a nice, new install.

Good luck!

---

### Post by Mr_VeRiTy on 2010-10-06
> **Rubi1200 said:**
> The perfect setup for a fresh install!

Delete the Lucid / partition, leaving /home untouched and then install Maverick into the free partition choosing to install / there.

You keep your /home with all your data and get a nice, new install.

Good luck!
But what about all the hidden folders in /home will they cause any problems when installing maverick, 'cos as far as i'm concerned they contain settings or something don't they?

---

### Post by psusi on 2010-10-06
You don't need to uninstall or delete anything.  Just boot up the maverick install, point it to your / partition, and check the format box.  Point it to your /home partition, and do NOT check the format box.

And you really should find a backup solution, or sooner or later you WILL loose your stuff.

---

### Post by Mr_VeRiTy on 2010-10-06
> **psusi said:**
> You don't need to uninstall or delete anything.  Just boot up the maverick install, point it to your / partition, and check the format box.  Point it to your /home partition, and do NOT check the format box.

And you really should find a backup solution, or sooner or later you WILL loose your stuff.
Thanks, and I'm working on a backup solution :)

---

### Post by t.rei on 2010-10-06
I recently upgraded to maverick using the updatemanager just to try it... worked like a charm. :)

Obviously I had to reinstall my proprietary graphics drivers, but thats not at all different to lucid.

I understand your reluctance, tho: I was surprised myself at not getting a single error. The way they handle 3rd party repositories now is to disable them during the upgrade, prompting you to check them later. Good way to do it!

---

