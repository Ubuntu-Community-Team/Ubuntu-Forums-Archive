---
title: "Jaunty Upgrade - dbus-daemon problem?"
date: 2009-03-16
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Jove on 2009-03-16
After an upgrade to Jaunty over the weekend, I'm experiencing some weirdness which only seems to apply to my main account. There are a few things that are possibly all inter-related, which are:

1. There are 2 instances of dbus-daemon, one running as my user and one as "messagebus" which are constantly running at about 20% CPU each meaning that system load is much higher than I would expect.
2. The bottom panel Window List applet fills up with hundreds of File Managers on login. Only way to kill this is to remove the panel.
3. Moving the pointer to the desktop background or any panel shows the spinning hourglass, as though something is still initializing.

I created a new account and it seems ok, so the issue is probably somewhere in .gconf or similar. Any clues as to where I should be looking?

Thanks,

Alan

---

### Post by Jove on 2009-03-16
After some more experimentation, the strangeness only seems to occur if I have /apps/nautilus/preferences/show_desktop unchecked (as required for Compiz wallpapers, I think). As soon as I uncheck this, the Window List applet starts filling up with hundreds of File Manager instances and dbus CPU utilization skyrockets. Weird, eh? If it's checked on, all seems good (except I can't see my Compiz wallpapers, of course). Any ideas?

---

### Post by Jove on 2009-03-16
Ahha - found this:

[https://bugs.launchpad.net/ubuntu/jaunty/+source/nautilus/+bug/325973](https://bugs.launchpad.net/ubuntu/jaunty/+source/nautilus/+bug/325973)

---

