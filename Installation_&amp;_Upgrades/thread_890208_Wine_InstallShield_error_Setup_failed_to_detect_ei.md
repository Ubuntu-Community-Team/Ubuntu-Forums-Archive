---
title: "Wine: InstallShield error: Setup failed to detect either Windows 95 or Windows NT 3.5"
date: 2008-08-14
forum: Installation &amp; Upgrades
---

### Post by spamking2000 on 2008-08-14
Hey, I'm trying to install an old Windows graphics suite but I'm not getting very far. This has to be a stupid error that would be easy to get around. I get the install sheild loading screen and then it immediately gives me an error:

Setup failed to detect either windows 95 or Windows NT 3.51 or later.

I noticed I don't seem to have a ~/.wine/config file. There are system.reg and user.reg files, but not config file like I've seen in other posts. Not sure what to do to create one. I can get to the configure wine app from the menu in Gnome, but I'm wondering if maybe it needs to save somewhere else as well.

Thanks!
spamking2000

---

### Post by bgerlich on 2008-08-14
Type winecfg in console, or press Alt+F2 and type in winecfg. Now change the system identification to win 95.

---

### Post by spamking2000 on 2008-08-15
Oh this is too weird. I did that in the winecfg for "setup.exe," but didn't change it globally. I changed it globally and it installed perfectly.

Here's a weird one though... I can open the program, but as soon as I open a file, it just quits. No idea why. There's no error. I've had this problem with other programs, but usually they've just resolved themselves. I've tried changing the default windows version from everything to Win95-XP and NT 3.5, 4.0 and Win2000. They all result in the same error.

The app is Micrografx Picture Publisher 6. Anyone have any ideas?

Thanks,
spamking2000

---

