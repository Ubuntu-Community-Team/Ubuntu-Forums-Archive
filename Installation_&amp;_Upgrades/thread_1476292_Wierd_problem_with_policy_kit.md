---
title: "Wierd problem with policy kit"
date: 2010-05-07
forum: Installation &amp; Upgrades
---

### Post by xfuser4 on 2010-05-07
I've tried to upgrade a system from 9.10 to 10.04 today. Unfortunately the upgrade failed before the cleanup process could start.

As a consequence I've got a really weird behavior now: all services which use PolicyKit fail somehow (no shutdown button in the GNOME menu; no legitimation dialog in preference panels etc.)

I've figured out, that I can temporarily solve the problem by doing:

apt-get purge policykit
apt-get install policykit

After restarting the system, PolicyKit will work. After another restart, the old problems appear again...

---

### Post by sisco311 on 2010-05-07
Is your system up to date now?

What's the error message you get when the apps fail?
```
pkexec echo error
```

---

### Post by xfuser4 on 2010-05-07
```
Error executing command as another user: No authentication agent was found.
```

---

### Post by sisco311 on 2010-05-07
> **xfuser4 said:**
> ```
Error executing command as another user: No authentication agent was found.
```

make sure that /usr/lib/policykit-1-gnome/polkit-gnome-authentication-agent-1 is running and it's added to the startup applications.

---

### Post by xfuser4 on 2010-05-07
I'm sorry. I was a little bit lazy and executed "pkexec" using "ssh -Y" which doesn't work...

If I execute it directly on the affected computer, then the legitimation dialog appears and works correctly.

On the other hand all legitimation dialogs of the preference panels and the shutdown button in the gnome main menu still do not appear...

---

### Post by xfuser4 on 2010-05-10
Okay, I was able to solve the issue by:

apt-get install --reinstall policykit-1

---

