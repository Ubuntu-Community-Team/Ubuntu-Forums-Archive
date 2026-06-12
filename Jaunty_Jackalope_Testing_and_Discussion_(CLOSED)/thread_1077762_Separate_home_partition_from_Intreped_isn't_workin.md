---
title: "Separate /home partition from Intreped isn't working"
date: 2009-02-22
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by davidself1001 on 2009-02-22
I have a separate /home partition and when I did an install of JJ I get strange happenings.  First when it comes up I don't get my background from Intreped.  Instead I get a royal blue screen.  I do have my panels as defined in Intreped though.  I also was able to determine that /home was correct by checking in places and in sys mon file systems.  Another thing that happens is that some process /app is being launched 100's of times (I get narrower and narrower vertical lines in my panel where I normally have buttons for launched apps.  this occurs for a minute or so then I am unable to do anything, I am completely locked up.  Can't do ctrl-alt-backspace or anything.  I also noticed that my theme from Intreped is also not utilized either (same issue as background probably).  Could there be something in compatible in my /home dir with JJ?

---

### Post by BwackNinja on 2009-02-22
You definitely have nautilus show_desktop disabled in gconf-editor. Re-enable it and all should be good.

just alt+f2 "killall nautilus"

then open gconf-editor

apps > nautilus > preferences > show_desktop

and enable it again. Its a known bug.

---

### Post by davidself1001 on 2009-03-31
> **BwackNinja said:**
> You definitely have nautilus show_desktop disabled in gconf-editor. Re-enable it and all should be good.

just alt+f2 "killall nautilus"

then open gconf-editor

apps > nautilus > preferences > show_desktop

and enable it again. Its a known bug.
Just upgraded to 9.04 beta and this bug still exists.  Is there a plan to correct this?  It is a bit minor but I prefer to have the show icons turned off so that my desktop is clean.

---

### Post by BGFG on 2009-03-31
> **davidself1001 said:**
> Just upgraded to 9.04 beta and this bug still exists.  Is there a plan to correct this?  It is a bit minor but I prefer to have the show icons turned off so that my desktop is clean.

I think it's obvious that there is a plan to correct it :) i'm waiting on it also, every time i get updates, even if the updates have nothing to do with nautilus or gnome, I race across to gconf and turn the setting off, then the windows start to pop up and I turn it back on...

---

