---
title: "Ubuntu release upgrade fails"
date: 2018-05-10
forum: Installation &amp; Upgrades
---

### Post by minashokry on 2018-05-10
Hi..

I am having an issue with running the check for update script. Every time I run "/usr/lib/ubuntu-release-upgrader/check-new-release-gtk", I get an error like this
```

/usr/lib/ubuntu-release-upgrader/check-new-release-gtk:30: PyGIWarning: Gtk was imported without specifying a version first. Use gi.require_version('Gtk', '4.0') before import to ensure that the right version gets loaded.
  from gi.repository import Gtk
Traceback (most recent call last):
  File "/usr/lib/ubuntu-release-upgrader/check-new-release-gtk", line 165, in <module>
    Gtk.init_check(sys.argv)
TypeError: Gtk.init_check() takes exactly 0 arguments (1 given)

```

I can understand the error, but I don't know why this is happening. Something doesn't seem right.. Anyone can help?
BTW, this happens with both unity and default desktop. I am on ubuntu 18.04. This was happening on 17.10, I managed to to upgrade somehow (using the QT version) and was hoping this apparent version mismatch issue will go with the upgrade, but it didn't happen.

---

### Post by dino99 on 2018-05-10
You might want to clean the system via 'bleachbit' (as root, carefully select options) and rebbot. If the problem persist, then login with an other user (avoid ubity (abandonware) and wayland session (not fully working yet) to know if your own profile is clean or not.

The pygiwarning is a 'warning' fully harmless (a todo dev's work) :D

---

### Post by minashokry on 2018-05-11
Hi.. First thanks for the response.

Then I tried th bleachbit as root, and I tried a new user without ubity and wayland. Same thing is still happening.. Any advice?

---

