---
title: "suspend from command line in karmic"
date: 2009-10-16
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by CStick on 2009-10-16
how do i suspend my laptop from command line in karmic ?

i've tried 
```
dbus-send --session --dest=org.gnome.PowerManager --type=method_call --print-reply --reply-timeout=2000 /org/gnome/PowerManager org.gnome.PowerManager.Suspend
```but it dose not work.

---

### Post by scorp123 on 2009-10-17
```
/usr/sbin/pm-suspend
```

... At least this used to work on Jaunty. No idea if it's still the same on Karmic.

The manual:
```
man pm-suspend
```

---

### Post by CStick on 2009-10-17
> **scorp123 said:**
> ```
/usr/sbin/pm-suspend
```... At least this used to work on Jaunty. No idea if it's still the same on Karmic.

The manual:
```
man pm-suspend
```


yeah , that also works on karmic :P

---

