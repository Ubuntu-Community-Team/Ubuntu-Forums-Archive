---
title: "How do I delete Gnome-panel only without deleting gnome?"
date: 2010-03-02
forum: Installation &amp; Upgrades
---

### Post by ki4jgt on 2010-03-02
I don't want gnome-panel

---

### Post by zeroseven0183 on 2010-03-02
What do you want?

Here's a way to eliminate the gnome-panel totally
1. press Alt + F2
2. type gconf-editor
3. go to desktop > gnome > session > required_components
4. right-click panel and select Edit Key...
5. remove the entry gnome-panel and
6. press OK
7. log-off then log-in

---

