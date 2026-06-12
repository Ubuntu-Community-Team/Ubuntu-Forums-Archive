---
title: "How to kill X ?"
date: 2009-10-20
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by ayates on 2009-10-20
When I go to a tty and try to kill gdm or X all it does is restart and throw me back to a login.
How do you stop this ? 

Thanks for any help.

---

### Post by dalonso on 2009-10-20
> **ayates said:**
> When I go to a tty and try to kill gdm or X all it does is restart and throw me back to a login.
How do you stop this ? 

Thanks for any help.

I cannot test it right now because I'm in the office. Anyway, in pre-karmic era you would do the following:

[INDENT]sudo /etc/init.d/xorg stop[/INDENT]

In Karmic, as it has been migrated to upstart, when you do the above it will warn you to use upstart service start/stop commands and will give you a hint about the exact command, something in the lines of:

[INDENT]sudo service xorg stop[/INDENT]

Again, as I cannot test it right now, I do not remember whether the xorg service is really called "xorg". So try it first with the "sudo /etc/init.d/xorg stop" command in order to get the warning and the tip about the "service XXXX stop" command.

---

### Post by Tibuda on 2009-10-20
You can set a shortcut to restart x in gnome.

---

### Post by lykwydchykyn on 2009-10-20
There's no xorg service.  You would stop gdm.

In Karmic you can do:
```

sudo /etc/init.d/gdm stop

```
or the much simpler:
```

sudo stop gdm

```

---

### Post by ayates on 2009-10-20
Duh. So simple.

Thanks everyone.

---

