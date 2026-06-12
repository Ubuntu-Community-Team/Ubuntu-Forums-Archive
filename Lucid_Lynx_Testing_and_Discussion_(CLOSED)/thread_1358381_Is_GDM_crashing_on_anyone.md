---
title: "Is GDM crashing on anyone?"
date: 2009-12-18
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Jordanwb on 2009-12-18
I've had GDM crash on me about 6 times while loading. Xorg says that it didn't detect my video card, keyboard or mouse. I find the later two hard to believe since this is a laptop. My video card is a Radeon X1200. When Xorg tells me that it couldn't figure.. it asks me if I want to go into low res mode, use last good config (which never works) or drop to shell (which never works either). Has anyone experiences this or got a fix for it?

---

### Post by DougieFresh4U on 2009-12-18
Well, I am still getting 'gdm broken' when updating. usplash is the cause I believe.
```
The following packages have unmet dependencies:
  gdm: Breaks: usplash but 0.5.51 is installed.
```

---

### Post by dino99 on 2009-12-18
nothing wrong here, i suppose something is not well installed.

try to remove / purge & reinstall gdm

---

### Post by Jguy on 2009-12-18
EDIT: I'm...in the wrong forum. I thought I was somewhere else. My apologies, my comment is not related to the discussion at hand.

---

### Post by Jordanwb on 2009-12-18
I replaced usplash with plymouth.

---

### Post by ranch hand on 2009-12-18
I use Plymouth too and it seems, at least on my box, to work a lot better.

---

### Post by Jordanwb on 2009-12-19
It just happened again and the screen is flashing, oh now it stopped flashing (famous first words). I'll try find a error log or something. I try to drop to a shell but I don't even get a terminal.

---

### Post by k3lt01 on 2009-12-19
My laptop decided it had a problem yesterday and forced me into "Low Res Mode". It looked no different to normal though. Since then I removed everything associated with Compiz, I don't use its functionality anyway so its no loss to me, and I haven't had a problem since.

---

### Post by autark on 2009-12-19
These last few days I've had gdm crash on me a couple of times in early startup. After reboot it will work fine again. I haven't got Plymouth installed, and usplash was uninstalled some time ago.

---

### Post by Jordanwb on 2009-12-19
I've reinstalled but decided not to upgrade anything until libesd-alsa0 is updated. Until that package is updated no new gnome packages will be updated.

---

