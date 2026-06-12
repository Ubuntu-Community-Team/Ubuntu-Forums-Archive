---
title: "Delete Evolution config files in Karmic"
date: 2009-10-04
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by seanlano on 2009-10-04
This might sound strange, but I can't seem to delete my Evolution config. I'm using the Karmic beta, and I tried to copy across my ~/.evolution folder from my Jaunty home partition, but Evolution kept bringing up the "New account" dialogue, so I entered a bunch of gibberish, and now I can't get rid of it. I have tried multiple times to delete the ~./evolution folder in Karmic, but Evolution seems to resurrect it every time I run it. It must have some cache somewhere, which it reverts to when it notices the ~./evolution folder is gone, but even if I delete the "bad" ./evolution folder and replace it with the "good" folder from the other partition, it still brings back the "bad" config! How can I kill this config?

---

### Post by lenticular on 2009-10-15
I have run into this before and although I can't find the thread that helped me out, I believe that it comes down to nuking evolution files outside of .evolution. For me, I believe that it was  .gconf/apps/evolution.  This thread, about backing up evolution, also mentions  .gnome2_private.
 [http://ubuntuforums.org/showthread.php?t=1222940&highlight=evolution+gconf](http://ubuntuforums.org/showthread.php?t=1222940&highlight=evolution+gconf)

You will probably do better to find a more precise thread that actually covers the problem, but I thought this might be helpful.

Good luck.

---

### Post by seanlano on 2009-10-16
I managed to sort-of bypass the problem, by importing the backup I made of Evolution in Jaunty, then deleting the gibberish account from the Settings menu in Evolution. It works fine now, but it doesn't explain why this happens. Some sort of fail-safe, I guess.

---

