---
title: "Live CD kicks me out during install"
date: 2008-05-11
forum: Installation &amp; Upgrades
---

### Post by Hnefi on 2008-05-11
Heyall.

Trying to install Ubuntu 8.04 on an AMD 3800+. After choosing language settings, partitions etc, the live CD environment starts up. I start the "Install" script, go through the language settings, partitions etc again (why?), and the system starts copying files to the HD.

However, about halfway through the copying, the system kicks me out and shows me the login screen, with a message saying "User Ubuntu will login in 10 seconds". Needless to say, when the system lets me back in, the install procedure has been aborted and various errors occur (elements of the desktop are missing).

What the heck is going on?

---

### Post by wpshooter on 2008-05-11
Did you check the integrity of your Ubuntu CD by running the verification function that is found on the initial Ubuntu boot screen menu ?

---

### Post by Hnefi on 2008-05-11
I did. No errors.

I switched from the AMD64 CD to the x86 CD. It worked.

I think there's a bug on the AMD64 CD, because the x86 CD simply let me configure the system and then installed it. The AMD 64 CD always unnessecarily booted the Live system first, then let me attempt to install from within that. It looks like the menu option for "Install Ubuntu" is the same as "Try without installing anything".

---

