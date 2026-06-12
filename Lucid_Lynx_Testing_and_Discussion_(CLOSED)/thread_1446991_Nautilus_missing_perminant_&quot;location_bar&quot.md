---
title: "Nautilus missing perminant &quot;location bar&quot;?"
date: 2010-04-04
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by toupeiro on 2010-04-04
I just noticed something sort of annoying with nautilus.

In the past, you have the option of selecting "block" type location paths in the location bar, with a square you could click on at each level in the directory structure, but you also had the option of permanently setting a location path bar where you could type, and tab-to-complete, your desired path.  Now, it looks like the only way to get that at all is to press ctrl-L, and as soon as you type in a path, you lose that bar alltogether until you press ctrl-L again.  Is there any way to get this to anchor back permanently to the nautilus file browser?  This was great functionality that is kind of annoying to have to use a keystroke combination to use every time which was not the case prior to 9.10.

Thanks in advance!

-T.

---

### Post by jpeddicord on 2010-04-04
```
gconftool -t bool -s /apps/nautilus/preferences/always_use_location_entry true
```

(that's the /apps/nautilus/preferences/always_use_location_entry checkbox/key in gconf-editor, if you prefer to change it that way.)

---

