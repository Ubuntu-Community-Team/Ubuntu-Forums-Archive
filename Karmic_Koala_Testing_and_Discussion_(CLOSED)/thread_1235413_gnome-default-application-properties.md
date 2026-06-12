---
title: "gnome-default-application-properties"
date: 2009-08-09
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by taavikko on 2009-08-09
Has someone else noticed that this misses the settings applied to it?
At least in "web browser"

Example, I'm running arora as a browser, setting it to default app.
This setting is immediately lost when closing the g-d-a-p app...

arora just got an update that it can be enabled in update-alternatives, unfortunately this doesn't work in all the places (yet)

---

### Post by cdEWoozy on 2009-08-09
Known bug. Your settings are saved and applied, but if you re-open g-d-a-p it resets all entries.

[https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/403671](https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/403671)
[http://bugzilla.gnome.org/show_bug.cgi?id=590316](http://bugzilla.gnome.org/show_bug.cgi?id=590316)

---

### Post by taavikko on 2009-08-09
> **cdEWoozy said:**
> Known bug. Your settings are saved and applied, but if you re-open g-d-a-p it resets all entries.

[https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/403671](https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/403671)
[http://bugzilla.gnome.org/show_bug.cgi?id=590316](http://bugzilla.gnome.org/show_bug.cgi?id=590316)

Thanks.
should always check the LP/gnome.bugzilla before posting, but.... lazyness :)

---

