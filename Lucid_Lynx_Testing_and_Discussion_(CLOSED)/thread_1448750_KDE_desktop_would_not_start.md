---
title: "KDE desktop would not start"
date: 2010-04-07
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by atlee on 2010-04-07
I picked up a bug 2 days ago, i decided to remove the blacklist of Nouveau after the Plymouthd update so many days ago and this is what happened, computer rebooted but without the desktop, abit like booting into dos but showed me with a terminal type screen with login and password, i'm guessing the KDE GUI didn't load? I tryed restarting 3 times and it didn't fix it, Tryed Sudo start gdm and the screen flickered 5-6 times then went back to terminal like screen.

Had enough of that business turned machine off, went to bed woke up next day then it booted into the desktop with the graphics failing, so added the Nouveau blacklist again to get 3d acceleration again.

Anywhere on Ubuntu that shows logs of this incident then i can show you guys/girls what i'm talking about here.

---

### Post by Gregorybekkers on 2010-04-07
Can u load it with "startx"? 
else try to:   sudo apt-get install kubuntu-desktop

---

### Post by atlee on 2010-04-07
I'm up and running now but i think it was one of the patches that cause my KDE desktop not to load, anyway thanks.

---

