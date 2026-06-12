---
title: "gnome-terminal and geometry"
date: 2009-08-25
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by taavikko on 2009-08-25
Anyone else affected?

Trying to launch gnome-terminal with predefined geometry in the launcher
and HSIZExXSIZE is not honoured.
XPOS+YPOS works as expected.

```
gnome-terminal --geometry=100x32+15+70
```

Previous version worked correctly.

---

### Post by tekstr1der on 2009-08-25
All parameters are being accepted here. Works as expected.

---

### Post by taavikko on 2009-08-25
> **tekstr1der said:**
> All parameters are being accepted here. Works as expected.

Went ahead and cleaned ~/. for settings.
Switched to Human theme,
And this is the result->

---

### Post by taavikko on 2009-08-25
Reported: #[418555](https://bugs.edge.launchpad.net/ubuntu/+source/gnome-terminal/+bug/418555)

---

### Post by tekstr1der on 2009-08-25
My bad, you are correct taavikko. Needed to reboot to see this.

---

