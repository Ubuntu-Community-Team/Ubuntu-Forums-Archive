---
title: "/etc/init.d/bluez-utils deleted"
date: 2005-06-16
forum: Installation &amp; Upgrades
---

### Post by Osmodia on 2005-06-16
I have deleted this two files:

/etc/init.d/bluez-utils
/etc/default/bluez-utils

How can I recover them?

---

### Post by imightbegiant on 2005-06-16
[QUOTE=Osmodia]I have deleted this two files:

/etc/init.d/bluez-utils
/etc/default/bluez-utils

How can I recover them?[/QUOTE]
 A quick reinstall of the bluez-utils package should replace them if they were the default files

$sudo apt-get install --reinstall bluez-utils

but if you just deleted them from the window manager, you can open up the trashcan from the icon on the gnome panel and pull them out.

---

### Post by Osmodia on 2005-06-16
I've reinstalled the module with "apt-get install --reinstall bluez-utils", but the two files doesn't seem to appear.

Can you copy+paste them?

---

### Post by imightbegiant on 2005-06-16
I tested it out and this *will* work:
```
$sudo apt-get remove --purge bluez-utils
$sudo apt-get install bluez-utils
```

---

### Post by Osmodia on 2005-06-17
Thank you.

Removing bluez-utils with "--purge" works.

---

