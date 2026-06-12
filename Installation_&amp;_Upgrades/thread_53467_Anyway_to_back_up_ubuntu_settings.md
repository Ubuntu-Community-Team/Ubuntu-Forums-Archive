---
title: "Anyway to back up ubuntu settings?"
date: 2005-07-31
forum: Installation &amp; Upgrades
---

### Post by PrimoTurbo on 2005-07-31
I'm wondering if there is anyway to backup my ubuntu setup. I have a bunch of custom stuff happening and I would hate if I loose it due to messing around more. Anyway I can back everything on a bunch of cd-r's?

---

### Post by Xian on 2005-08-01
When you say your ubuntu setup are you talking about just your personal settings or an entire system backup?

---

### Post by jasmuz on 2005-08-01
You could back up everything you have downloaded so far, so if it comes time to reinstalling again just place them in the original folder and voilá, Zero downloading time!

I meant copy /var/cache/apt/archives

That is where apt keeps all the .deb files it has downloaded

PS: you could also make a copy of your hidden files in your /home directory, wich are the settings for your user.

---

### Post by Sam on 2005-08-01
[QUOTE=PrimoTurbo]I'm wondering if there is anyway to backup my ubuntu setup. I have a bunch of custom stuff happening and I would hate if I loose it due to messing around more. Anyway I can back everything on a bunch of cd-r's?[/QUOTE]
All your settings are stored in your home directory (under hidden directories like .gnome or .mozilla). If you mount the same home on an another box, the settings will be restored.

---

### Post by Wide on 2005-08-01
To recreate  a system I use [this approach](http://www.ubuntuforums.org/journal.php?do=showjournal&j=202) I have in my journal

Hope this helps  :)

---

