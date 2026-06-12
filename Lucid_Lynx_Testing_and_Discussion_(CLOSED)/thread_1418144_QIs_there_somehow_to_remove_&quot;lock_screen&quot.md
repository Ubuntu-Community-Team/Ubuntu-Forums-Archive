---
title: "Q:Is there somehow to remove &quot;lock screen&quot; and &quot;log out [user]&quot; in gnome main menu?"
date: 2010-02-28
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by agitdd99 on 2010-02-28
I'm testing out lucid alpha 3, and i want to remove those menu away. can't anybody please help me?

---

### Post by ghostborg on 2010-02-28
Thats strange, I just did a fresh install of Ubuntu 10.04 Alpha 3 and those menu items are not in my menu.

Because of that I could not verify this but you should be able to right click somewhere over your menu ex.Applications and select edit menus.
This will bring up a gui with boxes to uncheck those items you don't want.
Do not delete them just uncheck them so if you need them later they are still there.

---

### Post by agitdd99 on 2010-02-28
> **ghostborg said:**
> Thats strange, I just did a fresh install of Ubuntu 10.04 Alpha 3 and those menu items are not in my menu.
maybe you still have the default menu bar that consist of three main menu : APPLICATION, PLACES, and SYSTEM. I already replaced it with the main gnome menu from "add to panel" option.

[IMG]http://i242.photobucket.com/albums/ff296/agitdd99/Screenshot-2.png?t=1267407265[/IMG]

> **ghostborg said:**
> Because of that I could not verify this but you should be able to right click somewhere over your menu ex.Applications and select edit menus.
This will bring up a gui with boxes to uncheck those items you don't want.
Do not delete them just uncheck them so if you need them later they are still there.

You mean like this one?

[IMG]http://i242.photobucket.com/albums/ff296/agitdd99/Screenshot-1-1.png?t=1267407454[/IMG] 

I can't find anything to be unchecked. Is there any hints to change it in the gconf-editor application?

---

### Post by agitdd99 on 2010-02-28
Hey I already figured it out how. here are the hints:

1. press ALT+F2
2. Run "gconf-editor"
3. go to /apps/panel/global/
3. Check the following option : "disable_log_out" and "disable_lock_screen"

[IMG]http://i242.photobucket.com/albums/ff296/agitdd99/Screenshot-3.png?t=1267412933[/IMG]


But i found that's could be a bug or something. The "lock screen" menu is still there. while the "log out [user]..." and "shutdown.." menu is hidden.


[IMG]http://i242.photobucket.com/albums/ff296/agitdd99/Screenshot-1-2.png?t=1267413359[/IMG]

---

