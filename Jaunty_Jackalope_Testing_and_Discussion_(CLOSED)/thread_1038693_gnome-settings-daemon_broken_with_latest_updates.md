---
title: "gnome-settings-daemon broken with latest updates"
date: 2009-01-13
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Starks on 2009-01-13
Anyone else having g-s-d not working?

---

### Post by ronacc on 2009-01-13
I get that sometimes but it is usualy ok on the next boot .

---

### Post by danf_1979 on 2009-01-13
> **Starks said:**
> Anyone else having g-s-d not working?

Hi, try deleting ~/.config/monitors.xml if that exists.
Possibly bug [https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/309602](https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/309602)

---

### Post by simo on 2009-01-15
It only works on my comp when executed with sudo

---

### Post by ShirishAg75 on 2009-01-15
how do you know its broken. What tells you?

---

### Post by Starks on 2009-01-15
> **danf_1979 said:**
> Hi, try deleting ~/.config/monitors.xml if that exists.
Possibly bug [https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/309602](https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/309602)

that fixed it.

---

