---
title: "Update from 3/39 killed gnome"
date: 2009-04-02
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by hanover.fiste on 2009-04-02
I can login and the gnome desktop backgroupd appears, windows have borders so I know the WM is running, but I get no icons and no menus. gnome-splash never seems to start, either. I tried killing my .gnome* and .gconf* dirs to see if something didn't upgrade right, but that got me nothing other than a pop-up at login stating that gnome-fastuser-switching was having problems starting, and asking if I wanted to remove it from my configuration. Whether I do or not, it makes no difference. Anyone run into this or have an idea of how to fix it?

---

### Post by hanover.fiste on 2009-04-04
Beuler? Beuler?

---

### Post by llamakc on 2009-04-04
Check to see if Nautilus is running.

```

ps aux | grep nautilus

```

Is it running with the `--no-desktop` flag?

---

