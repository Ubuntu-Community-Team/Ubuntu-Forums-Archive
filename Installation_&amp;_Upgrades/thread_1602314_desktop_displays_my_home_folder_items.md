---
title: "desktop displays my home folder items"
date: 2010-10-21
forum: Installation &amp; Upgrades
---

### Post by rvchari on 2010-10-21
hi everybody, this is my first ever post on the forum.
long ago when i upgraded from jaunty to lucid, everything was fine when suddenly one day i found my desktop flooded with my home folder contents. i was trying a lot of juglery but no result. finally i went to gconf-editor and unchecked the show desktop menu on apps > nautilus > preferences.

recently i upgraded from lucid to maverick. felt the problem will b resolved but it is still such. anyone to guide me here ?

thanx in advance

---

### Post by luvshines on 2010-10-21
Check if this is ticked, untick it
```

gconf-editor
apps > nautilus > preferences > desktop_is_home_dir
```

---

### Post by rvchari on 2010-10-22
i have done all the jugglery buddy.... desktop_is_home_directory checked / unchecked. i still feel something is to be done in gconf_editor itself. i created a new username and its performing just fine. i even tried by deleting the .nautilus file thats created in home directory. still no issues:confused:
only posssible way is by unchecking the show_desktop. if i do this then the right clik option wont b activated !!!

---

