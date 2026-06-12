---
title: "Last upgrade results in failure of dbus"
date: 2006-09-20
forum: Installation &amp; Upgrades
---

### Post by fbronx on 2006-09-20
After the latest kernel upgrade I get the following error in the ./xsession-errors:

```

Failed to start message bus: Error in file /etc/dbus-1/session.conf, line 1n column 0: u

EOF in dbus-launch reading address from daemon
```

Also all my font-settings are changed.

---

### Post by fbronx on 2006-09-21
Installation of other packages always fails because of this:

```

Setting up dbus (0.60-6ubuntu8) ...

Starting system message bus dbus
Failed to start message bus: Error in file /etc/dbus-1/session.conf, line 1n column 0: u
```

Am I the only one who has this problem?

---

### Post by fbronx on 2006-09-21
The weird thing is that when I start gedit at the terminal I get the following error:

bronx@bronx-laptop:~/expat-2.0.0$ gedit README
Fontconfig error: line 1: u
Fontconfig error: Cannot load default config file

Look the first line. It contains the same error as the dbus configuration. What is used to read those configuration files?

---

