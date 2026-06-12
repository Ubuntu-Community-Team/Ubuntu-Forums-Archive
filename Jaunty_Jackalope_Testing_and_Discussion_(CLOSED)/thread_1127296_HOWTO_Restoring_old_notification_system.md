---
title: "HOWTO: Restoring old notification system"
date: 2009-04-16
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Caligula on 2009-04-16
As a lot of people are disappointed by the new notification system, I thought to post a (really) small howto on how to restore the good old ones.

Most people won't need this, but oh well.

First remove the *notify OSD* package.

```
sudo apt-get remove notify-osd
```

after this just install the old ones.

```
sudo apt-get install notification-daemon
```

Now all that's left is to kill the process -
```
killall notify-osd
```
and start the new one,
```
notification-daemon
```

That's it, you should have the old notifications now ;)

---

### Post by gali98 on 2009-04-16
I really like the new system notification system. :( I'm not seeing why people don't like it, but thanks for the tutorial.
That's the thing I love about linux. If you don't like something fix it :)
Thanks,
Kory

---

