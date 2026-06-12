---
title: "/etc/xdg/autostart missing items?"
date: 2009-10-25
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by ch6574 on 2009-10-25
Hi,

Certain apps (like Gwibber) will place a file under /etc/xdg/autostart/, often this will have the following set:

> X-GNOME-Autostart-enabled=false

Thereby not automatically starting the app by default on login, but which makes it easy for people to enable them to do so by "ticking" the disabled entry in the list under Preferences -> Startup Applications.

Other apps (like Empathy, iBus, etc) do not come packaged with these entries, so to automatically start them you need to find the actual binary name and manually configure an entry (or put a file under ~/.config/autostart).  Neither of these options is particularly intuitive.

Anyone else have this, or is this a known bug?

Thanks,
Chris

---

### Post by ch6574 on 2009-10-25
Seems there is a related bug open on a related topic

[https://bugs.launchpad.net/ubuntu/+source/empathy/+bug/322314](https://bugs.launchpad.net/ubuntu/+source/empathy/+bug/322314)

---

