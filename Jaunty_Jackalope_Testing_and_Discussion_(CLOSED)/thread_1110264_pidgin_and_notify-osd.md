---
title: "pidgin and notify-osd"
date: 2009-03-29
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by biasquez on 2009-03-29
hi i have 2 questions:
- pidgin-libnotify works fine with notify-osd?
- now i'm using pidgin devel version and i want to use pidgin-libnotify with notify-osd, i'm downloaded pidgin-libnotify with apt-get source from jaunty and compiled/installed it but i have old notify system. can i fix it?

---

### Post by syko21 on 2009-03-29
There is no reason to compile any of this from source.

Enter these into gnome-terminal

```
sudo apt-get install libnotify1 pidgin-libnotify
```

To enable notifications in pidgin
1. Open up Pidgin and goto the buddy list
2. Choose menu item Tools -> Plugins
3. Enable the plugin "Libnotify Popups"

---

### Post by biasquez on 2009-03-29
> **syko21 said:**
> There is no reason to compile any of this from source.

Enter these into gnome-terminal

```
sudo apt-get install libnotify1 pidgin-libnotify
```

To enable notifications in pidgin
1. Open up Pidgin and goto the buddy list
2. Choose menu item Tools -> Plugins
3. Enable the plugin "Libnotify Popups"


no, if i try to install pidgin-libnotify, apt-get overwrites my pidgin customized...

---

### Post by syko21 on 2009-03-29
then just install libnotify1. Then install plugin from source as you did before. It should appear in pidgin's plugin menu.

---

### Post by biasquez on 2009-03-29
> **syko21 said:**
> then just install libnotify1. Then install plugin from source as you did before. It should appear in pidgin's plugin menu.

but plugin appears in pidgin's menu, i enabled it but i don't have new notification managed by notify-osd but old notification, like ubuntu intrepid...

---

