---
title: "Keyboard Shortcuts - Super Key Bring Down Menu?..."
date: 2009-10-12
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by beastrace91 on 2009-10-12
So in Jaunty I was able to go into keyboard shortcuts and set my super key to pop up my gnome applications menu (so it is like the "windows" key) how ever now in Karmic it will not let me do so - it requires that I press a second key in addition to the super key...

Any one know if there is a way I can set it to JUST the super key again?

Thanks,
~Jeff

---

### Post by cyberkilla on 2009-10-12
I have *never* been able to do that. Someone told me that the Super key is just a modifier in GNOME, so it can't be used alone without serious trickery.

---

### Post by beastrace91 on 2009-10-12
It works just fine on my Jaunty install:

[IMG]http://i37.tinypic.com/2it4k8y.png[/IMG]

Any ideas why I can't do this on Karmic?

~Jeff

---

### Post by Aearenda on 2009-10-12
Fortunately, you can still do this using gconf-editor in Karmic. Find the key named /apps/metacity/global_keybindings/panel_main_menu and set its value to Super_L (note the underscore).

---

### Post by beastrace91 on 2009-10-12
Ahh thank you. I've never used gconf-editor before - it worked like a charm! For some reason on the keyboard shortcuts on Karmic detects my Super key as "Mod 4" instead of Super_L

~Jeff

---

