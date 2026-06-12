---
title: "KDM and GDM won't log in (single user mode is fine)"
date: 2009-04-09
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by jmite on 2009-04-09
On the Jaunty Beta, which was working fine for about a week, suddenly it won't log in. I can use single user mode fine, but neither KDM or GDM will log in. My wallpaper shows up, my mouse theme loads, and after about 5 seconds the screen goes back to the startup terminal, then goes back to the Dm login screen.

I don't know if this is a user problem, or an xorg problem. If it makes any difference I use Intel Graphics...

I can include the contents of files/outputs of commands, but frankly at this point I don't know what would be useful to you...
thanks!

---

### Post by knattlhuber on 2009-04-09
To differentiate if that is a user or xorg problem, you could create a new user from the commandline and try to log in graphically with the new account.

```
sudo useradd johndoe
```

---

### Post by jmite on 2009-04-10
I did so, and it logged in just fine as the new user, so there must be a problem with a config file in my home directory...

---

### Post by knattlhuber on 2009-04-10
You could try to log in and then post the output of
```
cat /var/log/syslog
```
That should give us an idea where the problem lies. Hopefully.

---

