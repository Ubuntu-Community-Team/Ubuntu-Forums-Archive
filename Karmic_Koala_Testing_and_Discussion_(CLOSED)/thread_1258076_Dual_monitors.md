---
title: "Dual monitors"
date: 2009-09-04
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by cykotiktek on 2009-09-04
I am running dual monitors just loaded alpha 5 on my system and i went into the new display settings and i can not get the settings to save my dual monitor setup.  I was wondering if i am doing something wrong it does say to log out and back in to save the settings i have done this several times including trying to reboot it to save the settings. 

Sorry i can't check for bugs i am at work so i am unsure if this is a known issue or not.

---

### Post by doas777 on 2009-09-04
I assume you are invoking your settings application with administrative privledges (eg gksu) ?

---

### Post by cykotiktek on 2009-09-08
I tried that and i am still getting the same result tells me to logout and log back in and then it still mirrors the two monitors.

---

### Post by bobince on 2009-09-08
What's in your ~/.config/monitors.xml? What's in your /etc/X11/xorg.conf (if you have one)?

---

### Post by cykotiktek on 2009-09-08
Well I got it set up now it was a problem with the resolution that i was trying to run.  I am running 1024x768 now and i would like to run 1280x1024 which is what it was set at in the past.

---

