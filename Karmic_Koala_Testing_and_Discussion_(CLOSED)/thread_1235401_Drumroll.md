---
title: "Drumroll"
date: 2009-08-09
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by theozzlives on 2009-08-09
I noticed they put "login window" back in the menus. I click on it and a dialog pops up for a split second, then it's gone.

I miss the drumroll at login, is there a command line to get it back? My GDM sound is active in my gconf-editor.

---

### Post by taavikko on 2009-08-09
> **theozzlives said:**
> I noticed they put "login window" back in the menus. I click on it and a dialog pops up for a split second, then it's gone.

I miss the drumroll at login, is there a command line to get it back? My GDM sound is active in my gconf-editor.

for the gdmsetup: [https://bugs.launchpad.net/bugs/410475](https://bugs.launchpad.net/bugs/410475)

What I could gather, atm the only sound setup is /desktop/gnome/sound/event_sounds
for enabling the sound events. Which can be done also in System->Sound

---

### Post by theozzlives on 2009-08-09
> **taavikko said:**
> for the gdmsetup: [https://bugs.launchpad.net/bugs/410475](https://bugs.launchpad.net/bugs/410475)

What I could gather, atm the only sound setup is /desktop/gnome/sound/event_sounds
for enabling the sound events. Which can be done also in System->Sound

Thanks, but that didn't answer my question. I already know the GUI part crashes.

---

### Post by scaine on 2009-08-09
That's odd - works fine here.  Unlock, everything.  I'd already hacked my gconf-editor to automatically log me in though, so perhaps it's that.

---

### Post by theozzlives on 2009-08-14
Bump

---

### Post by Marat89 on 2009-08-14
to Drumroll: I think this was a papercut, and they fixed it by removing it

---

