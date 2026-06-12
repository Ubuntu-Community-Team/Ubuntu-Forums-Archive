---
title: "Auto login into KDE with GDM ?"
date: 2009-08-25
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by vikrant82 on 2009-08-25
I have both gnome and kde installed and I am facing some problems setting kdm as default display manager. The problem is kdm won't start up if I set it as default (thrown to bash on start up.)

Well, I really dont care about my display manager. All I want is to be able to **auto login into KDE. **

/etc/gdm/custom.conf doesn't seem to care about "DefaultSession" key ..

Any clues.

---

### Post by Cenotaph on 2009-08-25
I don't have karmic installed right now, but i think there is some file under /etc/X11/ with the default desktop manager.

It probably says /usr/sbin/gdm, change it to /usr/bin/kdm

---

### Post by vikrant82 on 2009-08-26
Yea, you are right but this isn't working. If I use kdm as default display manager, I am just thrown at bash prompt to login.

---

### Post by Cenotaph on 2009-08-26
The way I remember from a similar experience i had with karmic was that KDM was not starting properly because that file always listed gdm as the default. After changing the content and a reboot it worked ok.

I might be forgetting something though.

As far as setting GDM up to start KDE automatically i don't think i can help you with that, sorry.

---

### Post by vikrant82 on 2009-08-26
I have tried by manually editing /etc/X11/default-display-manager. That doesn't work. I am sure it used to work before.

---

### Post by vikrant82 on 2009-08-26
bump

---

### Post by Lubia Garora on 2009-08-26
It is new for me i never read about  kde with gdm

---

### Post by trebach on 2009-08-27
You may not have installed enough of KDE for kdm to move to the desktop.

---

### Post by NCLI on 2009-08-27
Treback may be right, have you installed the complete kubuntu-desktop meta-package?

---

### Post by vikrant82 on 2009-08-28
Yup.. Got it working .. I did have kubuntu-desktop package, but for some reasons I had to reinstall kde again. That did it.

---

