---
title: "KARMIC alpha 5:  ALT-TAB not working"
date: 2009-09-07
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by popeil on 2009-09-07
Hello again, I've been having trouble using alt-tab to switch apps on Karmic.  I saw a couple of posts regarding Compiz and this problem - but not sure it applies here (?)...  I did reboot the system and still no alt-tab.

Any ideas?  Thaniks in advance

---

### Post by Slodeine on 2009-09-07
Same problem here.

Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)

---

### Post by drs305 on 2009-09-07
Are you talking about *outside* of Compiz? If so, I'm not having that problem. You should probably check System, Preferences, Keyboard Shortcuts: Window Management > Move between windows.

as well as 
```

gconf-editor /apps/metacity/global_keybindings/switch_windows

```

If they are wrong, it may be a bug unless you remember changing the values at some point.

---

