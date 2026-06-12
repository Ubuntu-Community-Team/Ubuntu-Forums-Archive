---
title: "Does Anyone Else See The Splash Screen Before KDM?"
date: 2009-09-28
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by jlacroix on 2009-09-28
This is really strange, when I start up my computer I see KDE's logon splash screen, and then KDM. After I log in, I am shown the splash screen again which continues on. I think it does this on my laptop too, and it looks really strange and out of place. Is it this way for anyone else?

---

### Post by MKdx on 2009-09-28
I saw something like this a week ago (?) in Ubuntu when the new GDM theme first uploaded. I'll disable autologin later tonight and see if it's still like that.

---

### Post by slakkie on 2009-09-28
Dunno, have to reboot too see. brb

---

### Post by koso on 2009-09-28
This happens for about 1 month. They are probably trying to start ksplashx as soon as posible (and replace usplash). 

This pre-KDM splash is started using KDM script (somewhere in /etc) so you can try to disable it, or probably change theme, becase now it is hardcoded to use Default oxygen theme, which can be quiet disturbing, especially if your KDM and KDE splash themes are different.

---

### Post by descendent87 on 2009-09-28
Is this different to the new ubuntu splash? If so how do I set it so the Kubuntu splash shows up instead of the ubuntu one (have both ubuntu-desktop and kubuntu-desktop installed) so I can have a look?

---

### Post by koso on 2009-09-28
> **descendent87 said:**
> Is this different to the new ubuntu splash? If so how do I set it so the Kubuntu splash shows up instead of the ubuntu one (have both ubuntu-desktop and kubuntu-desktop installed) so I can have a look?

It is different, but not functional yet. It is started by KDM (so you must switch from GDM). Problem is, that it is started only little time before KDM (in my case about 500ms), so you will see only blink. At this time it is far away from ubuntus functionality, and there is no reason to look at it :D

---

### Post by descendent87 on 2009-09-28
Thanks, think i'll wait until I can actually see it before trying

---

### Post by jlacroix on 2009-09-28
Yeah for me it's a few seconds. I don't have this problem on any other distro so this is Karmic-specific.

---

