---
title: "having problems with glade while opening update update-manager"
date: 2006-12-26
forum: Installation &amp; Upgrades
---

### Post by lighty206 on 2006-12-26
Hey,
I want to upgrade dapper to edgy, I want to use:
```
gksu "update-manager -c" 
```

I'm getting an odd error message:
```
$ gksu "update-manager -c"
Traceback (most recent call last):
  File "/usr/bin/update-manager", line 29, in ?
    import gtk.glade
ImportError: No module named glade
```

I have python-glade and all the other related packages that I thought about.

I'm not sure that its update-manager's fault because gmail-notify gives a similar error
```
$ gmail-notify
Traceback (most recent call last):
  File "./notifier.py", line 9, in ?
    from egg.trayicon import TrayIcon
ImportError: No module named egg.trayicon
```

What shall I do?
thanks a lot, lighty206.

---

### Post by Engnome on 2006-12-26
Well I can't solve your problem with update manager  but I can tell you how to upgrade to edgy though (but be warned, many people have problems with dapper -> edgy upgrade, be sure to have your desktop metapackage installed before trying an update)
```

gksudo gedit /etc/apt/sources.list
```

Replace all "dapper" with "edgy" (There is an inbuilt replace function)

---

