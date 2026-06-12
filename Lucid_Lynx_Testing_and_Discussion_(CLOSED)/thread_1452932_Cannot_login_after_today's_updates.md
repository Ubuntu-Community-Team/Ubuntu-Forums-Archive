---
title: "Cannot login after today's updates"
date: 2010-04-12
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by vikrant82 on 2010-04-12
Ok guys, Here I have a (kde + gnome) lucid box. I did whatever updates were there for today around 2 hours back and rebooted. I had kdm configured as default manager, with autologin enabled.

1. KDM doesn't load. It gets into a loop, loads, blacks and again loads.
2. I tried disabling auto login. Still same behavior/
3. Tried setting gdm as default manager. Manage to get the login screen, login into KDE. Crashes and gets thrown back to login screen.
4. Choose gnome and login - Same, gets thrown out on login screen
5. Create a new user and try to login. Logs in fine in gnome, and after 3-4 seconds everything freezes.

So how do we go about this one.

---

### Post by cosine352 on 2010-04-12
same here. can not login after update.

---

### Post by mervinb on 2010-04-12
I see almost exactly the same, except I use lxdm. I see lxdm trying to give me a login screen, but fails, blacks out, shows me the ubuntu progress screen, then attempts the login screen, ad infinatum.

Switching the display manager to gdm, I get the same as vikrant, but I actually get to a session (an LXDE session). The browser (firefox or chromium) starts. However when I load a web page, the browswer starts, but then screen blanks, and I'm thrown back into a gdm login screen. Other gtk programs seem to run ok.

Up to now, Lucid has been very stable for me, so this is a major regression.

Config: MSI Wind U100, Lucid (latest updates up to 12 April, when this problem occured).

---

### Post by bigsmitty64 on 2010-04-12
Same here, I get the splash screen, then blackout. I had to revert back to kernal 2.6.32.19 then booted fine.

---

### Post by Funnnny on 2010-04-12
Anyone have filed a bug in launchpad ? I have this problem too.

---

### Post by vikrant82 on 2010-04-13
This was fixed for me after latest updates this morning (5 hours back). I had to manually install, 2.6.32.20 as I had removed it yesterday as it was not completely installable due to dependencies problems. Today morning, I was able to install without any issues and 2.6.32.20 works fine now.

---

### Post by zenarcher on 2010-04-13
Working fine for me now, as well.

Cheers,
zenarcher

---

### Post by bigsmitty64 on 2010-04-13
> **zenarcher said:**
> Working fine for me now, as well.

Cheers,
zenarcher
ditto, short lived, whatever it was :)

---

