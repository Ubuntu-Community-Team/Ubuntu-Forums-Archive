---
title: "Freezes at login screen."
date: 2010-04-11
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by umby24 on 2010-04-11
I just saw that lucid beta 2 had been released, so i ran over to update manager, and found 400 MB worth of updates left to do. so I clicked update, and it ran its course, but it did happen to say that there was some url's it couldn't resolve, so i just skipped those packages, and let it install the rest.

It then asked me to reboot, so i did.

Ran as normal, some random shell crap popped up, no splash screen, then a login screen (whole process less than a minute), but at the login screen, nothing. It just froze up. None of the buttons on the keyboard responded. I tried a slightly earlier kernal, same effect. Booted from recovery, same issue. Logged in from console, not a problem.

I did notice though the tooltip (the little message under the mouse curser) popped up, then disappeared within about 3 seconds.

Compaq Presario c500 Laptop, if that helps any..

---

### Post by NightwishFan on 2010-04-11
My machine currently will not boot using the .20 kernel. At least not normally I did not wait to see 'if' it would boot, but no disk activity for at least a minute frozen on a console. the .19 kernel works,

---

### Post by cariboo on 2010-04-11
You obviously only did a partial upgrade. You may be able to fix it by starting in recovery mode, at the menu drop to root prompt with networking, then at the prompt type:

```
apt-get -f install
```

followed by:

```
apt-get update && apt-get dist-upgrade
```

---

### Post by umby24 on 2010-04-11
Ok, I managed to fix it, and at the time kernal -20 wasn't even installed.
I went into recovery (Kernal -19)  and ran the netshell, then apt-get update

it told me to run it again, so i did, and everything ran ok, then i typed in 'exit' and it went back to recovery menu, then i started dpkg to 'Repair broken packages'  and that fixed it.

---

