---
title: "menus cluttered, how to do reset to default?"
date: 2009-09-19
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by puccaso on 2009-09-19
normally, if my panel is messed up
i just delete the files related in my home dir, .gconf etc, and ubuntu re-creates the panel from the skel files, 

how do i reset the gnome menu's in the same way?

---

### Post by amauk on 2009-09-19
the menus are stored in gconf

```
rm -r ~/.gconf/apps/panel
```

---

### Post by jocko on 2009-09-19
> **puccaso said:**
> normally, if my panel is messed up
i just delete the files related in my home dir, .gconf etc, and ubuntu re-creates the panel from the skel files, 

how do i reset the gnome menu's in the same way?
Some of it can be fixed by removing the folder ~/.local/share/applications. At least it removed the extra clones of "add/remove" and "software sources" I have managed to accumulate in System-->Administration since I installed karmic...

---

