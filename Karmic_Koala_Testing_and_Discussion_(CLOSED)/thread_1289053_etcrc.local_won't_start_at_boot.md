---
title: "/etc/rc.local won't start at boot"
date: 2009-10-12
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by renkinjutsu on 2009-10-12
it's an executable ```
-rwxr-xr-x 1 root root 583 2009-09-25 03:19 /etc/rc.local
```

but the funny thing was, it executes properly when i do ```
sudo service rc.local start
or
sudo /etc/init.d/rc.local start
or
sudo /etc/rc.local
```

so i was curious and took a look at /var/log/messages with gedit and searched for "local" and it gave no indication that it loaded the scripts!

---

### Post by TerminX on 2009-10-12
Make sure the symlinks to /etc/init.d/rc.local are in /etc/rc[2-5].d... you should have, for example, a symlink from /etc/rc5.d/S99rc.local to /etc/init.d/rc.local, which is the script that actually executes /etc/rc.local.

---

### Post by renkinjutsu on 2009-10-12
yep.. the symlink is present.. =\ .. don't know what's wrong!

---

### Post by hanzomon4 on 2009-10-12
Not sure if this has anything to do with it but everything ha been moved to upstart jobs

---

