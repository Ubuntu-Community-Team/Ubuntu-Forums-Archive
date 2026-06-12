---
title: "udev won't conifugre after Karmic to Jaunty downgrade"
date: 2009-10-25
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Bit101 on 2009-10-25
After doing an a downgrade from karmic to jaunty, udev won't configure properly. It says
```

invoke-rc.d: initscript udev, action "restart" failed

```
after saying that it failed to start kernel event manager. I downgraded by changing the repos back to jaunty and apt-get dist-upgrade.

---

### Post by psyke83 on 2009-10-25
You cannot downgrade like that - it simply won't work.

Yes, you can try to force individual packages to downgrade, like so:

```
$ sudo apt-get install dbus/jaunty
```

However, *none* of the packaging scripts were written with downgrading in mind, so you will most likely encounter *many* difficulties.

---

### Post by FuturePilot on 2009-10-25
You can't downgrade. If you want to go back to Jaunty you're going to have to reinstall.

---

