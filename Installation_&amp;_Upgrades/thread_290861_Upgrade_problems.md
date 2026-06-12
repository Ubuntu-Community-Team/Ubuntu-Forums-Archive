---
title: "Upgrade problems"
date: 2006-11-01
forum: Installation &amp; Upgrades
---

### Post by jmags on 2006-11-01
I upgraded from Dapper to Edgy, and now xorg won't start. When I boot up I have a command line login, and when I try to use startx I get this:

```
xauth: creating new authority file /home/jmags/ .serverauth.4964
```

and there's a pause, and then
```

giving up.
xinit: Connection refused (errno 111): unable to connect to X server
xinit: No such process (errno 3): Server error.
```

---

### Post by taurus on 2006-11-01
See if you can reconfigure your X again with

```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by jmags on 2006-11-01
That got it, or pointed to it in any event. Thanks.

---

