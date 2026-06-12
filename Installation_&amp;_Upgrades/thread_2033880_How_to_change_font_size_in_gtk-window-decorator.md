---
title: "How to change font size in gtk-window-decorator"
date: 2012-07-27
forum: Installation &amp; Upgrades
---

### Post by gdesilva on 2012-07-27
Hi,

I am running Compiz under xfce4 and would like to know how to change the font size of the window titles which are set by gtk-window-decorator used by Compiz.

Thanks

---

### Post by gb2312 on 2013-01-25
I'm using debian, and found the gtk-window-decorator still uses metacity configurations, and these gconf settings seem to make it work:

gconftool-2 -s /apps/metacity/general/titlebar_font -t String "Sans Bold 9"
( You can set this only, but it doesn't look right)

gconftool-2 -s /apps/metacity/general/theme -t String "Clearlooks-Phenix"
( Similar to Clearlooks, but buttons are wrong)

gconftool-2 -s /apps/metacity/general/button_layout -t String "menu:mininize,maximize,close"

( With this, it looks like gnome2)

---

