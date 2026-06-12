---
title: "icons of running wine apps  do not appear on Dash after migration to 21.04"
date: 2021-11-04
forum: Installation &amp; Upgrades
---

### Post by gfyllos on 2021-11-04
After  upgraded to 21.04, running WINE apps such as wineconsole.exe do not appear on the Dash, as the used to under 20.04.

Can someone pls help re-enable  this function?

thank you very much!

---

### Post by TheFu on 2021-11-06
21.04 support ends in about 6 weeks.
Best to move to 21.10.

Of course, you could load 20.04 which has no-hassle support until 2025 April.

Understanding the difference between LTS and non-LTS releases is critical.

---

### Post by MAFoElffen on 2021-11-07
Try this first:
```

gsettings set org.gnome.desktop.background show-desktop-icons true

```
Restart the desktop by pressing <Alt><F2>, let go then enter <r>, then press <Enter>...

If that does not work, then right-click on the Desktop...  A context menu will appear.  At the bottom of the context menu click on  settings. A settings popup will appear. The top half is for  enabling/disabling. positioning, and sizing the desktop icons... One of those setting affects the desktop icons being visible.

Then upgrade the release to what will keep you with what will be supported (my disclaimer).

---

### Post by ActionParsnip on 2021-11-08
+1 for upgrade to 21.10 then retest

---

