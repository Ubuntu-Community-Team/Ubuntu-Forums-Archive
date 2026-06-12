---
title: "jaunty is showing &quot;starting file manager&quot; tabs when booting, alot of them"
date: 2009-02-11
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by whoop on 2009-02-11
When I booted Jaunty today, after I login I can see "starting file manager" tabs opening, and the amount is increasing and increasing. System is getting quite unresponsive. It wont even show the desktop wallpaper or desktop icons. 
Anybody have this problem?

---

### Post by douham on 2009-02-11
whoop, are you using the 2.6.28-7 or 28-6 kernel?

---

### Post by whoop on 2009-02-11
2.6.28-7

---

### Post by marmuta on 2009-02-11
Sounds like [#324925]("https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/324925"). The old thread was [http://ubuntuforums.org/showthread.php?t=1061458](http://ubuntuforums.org/showthread.php?t=1061458)
It stops spawning file browsers when you turn on /apps/nautilus/preferences/show_desktop in gconf-editor. Or try ```
gconftool-2 -s -t bool /apps/nautilus/preferences/show_desktop true
``` if the system is too busy for gconf-editor.

---

### Post by truonggiang231 on 2009-04-06
I have the same problem with Jaunty Beta. Don't know how to deal with this. I hope they will fix it in the final version

---

### Post by MaX on 2009-04-06
> **truonggiang231 said:**
> I have the same problem with Jaunty Beta. Don't know how to deal with this. I hope they will fix it in the final version

See the post above yours...

---

### Post by Labello on 2009-04-06
you could also use Ubuntu-Tweak an enable "Show Desktop Icons"

---

