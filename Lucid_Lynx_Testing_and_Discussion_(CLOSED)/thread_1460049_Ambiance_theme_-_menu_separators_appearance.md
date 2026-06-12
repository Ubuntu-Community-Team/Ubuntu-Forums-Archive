---
title: "Ambiance theme - menu separators appearance"
date: 2010-04-22
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by CryptoPaul on 2010-04-22
After a long time using the Human-Clearlooks theme Lucid's Ambiance was quite a change. 

One thing that really bugged me though was, to me at least, the poor visibility of the menu separators.

After a little digging around in the gtkrc file (located /usr/share/themes/Ambiance/gtk-2.0) I found that the style of these is controlled by:

```
style "separator-menu-item"
```

which starts around line #293

by changing

```
bg[NORMAL]= shade(0.4, @selected_bg_color)
```

to

```
bg[NORMAL]= shade(0.8, @selected_bg_color)
```

I was able to obtain the effect I was after...  maybe of use to someone else.

Regards - Paul

---

### Post by ubername on 2010-04-22
Thanks, done that, now much better.

---

