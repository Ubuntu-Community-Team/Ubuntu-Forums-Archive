---
title: "Lucid: Booting"
date: 2010-03-07
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by ccleanerfan on 2010-03-07
After I upgraded from Karmic to Lucid Alpha 3, when I boot, it goes to like a terminal-like black screen with an underscore on the top left. Only way to advance forward is by pressing the "enter" key. How do I prevent this from happening?

Also, how do I make it not go to the user selection? I made it so it doesn't ask for a password but I can't find the option for that other option.

Thanks.

---

### Post by patchwork on 2010-03-07
What happens if you press CTRL+ALT+F1 when you get the cursor?   It should drop you to the console.  If it does, log in and type

```
sudo service gdm stop && startx
```

This should bring you into the GUI.

---

