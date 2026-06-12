---
title: "gdm briefly flashes up during xsplash when autologin is enabled"
date: 2009-09-26
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by dinxter on 2009-09-26
the gdm login screen briefly flashes up and disappears during xsplash, i have it set to autologin. anyone else have this bug?  is there a bug open on it?

{EDIT} cant see one so...
[https://bugs.launchpad.net/ubuntu/+source/xsplash/+bug/437129](https://bugs.launchpad.net/ubuntu/+source/xsplash/+bug/437129)

---

### Post by martinpm24 on 2009-09-26
i have something similar, but i only see the background... The boot process show me first the gdm background, then the backgr change to the human theme and later show me my background.

---

### Post by Podex on 2009-09-26
Yes I saw this as well, thanks for creating the bug report. I guess I don't have any more information to add to it though, so I just did a 'this bug affects me too'.

---

### Post by dinxter on 2009-09-26
> **martinpm24 said:**
> i have something similar, but i only see the background... The boot process show me first the gdm background, then the backgr change to the human theme and later show me my background.
this sounds like the bug below, xsplash timing out before the users own background is set
[https://bugs.launchpad.net/ubuntu/+source/xsplash/+bug/435522](https://bugs.launchpad.net/ubuntu/+source/xsplash/+bug/435522)

---

### Post by VMC on 2009-09-26
> **dinxter said:**
> the gdm login screen briefly flashes up and disappears during xsplash, i have it set to autologin. anyone else have this bug?  is there a bug open on it?

{EDIT} cant see one so...
[https://bugs.launchpad.net/ubuntu/+source/xsplash/+bug/437129](https://bugs.launchpad.net/ubuntu/+source/xsplash/+bug/437129)

Thanks for reporting this bug. I tagged it "Affects me too". It's annoying.

---

### Post by kestal on 2009-09-26
I noticed this as well. Well, during xsplash boot my background flashes white a few times. Other times it loads up the gnome panels while still only seeing the throbber/xsplash background. Not sure if thats related or a separate bug.

With that said, if this has been fixed in any way I apologize.

---

### Post by dinxter on 2009-09-26
if someone has this bug, not the background one (thats triaged and assigned) could you mark it confirmed

---

