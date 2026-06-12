---
title: "restart kde from command line"
date: 2008-11-26
forum: Installation &amp; Upgrades
---

### Post by jackwarr on 2008-11-26
Help!  I accidently disabled or uninstalled KDM and now I get no grpahical interface, only a command line.  Kubuntu starts up, but I get no GUI.  I get the following text:

jack-desktop login:

I can type my user name and then it asks for my password, but then I get:

jack@jack-desktop:~$

How can I either a) restore my KDM or b) invoke GDM?

Please help.

Jack

---

### Post by Skripka on 2008-11-26
try this:

```
sudo /etc/init.d/kdm start
```

---

### Post by jackwarr on 2008-11-26
Thank you very much.  Worked great!

By the way, do you know how to switch back to GDM?

---

### Post by Skripka on 2008-11-26
> **jackwarr said:**
> Thank you very much.  Worked great!

By the way, do you know how to switch back to GDM?

That I do not know an easy GUI way of....odds are there is probably a setting somewhere for which login manager to use....If you just want GNOME and don't mind KDM, you can select a different session.

If all ELSE fails.....I don't like messing with KDM/GDM as boot scripts can get broken-and then need repaired and what not--those are my own worries though.

logout of Gnome/KDE, hit CRTL+ALT+F1...You'll get a command prompt

type:
```
sudo /etc/init.d/kdm stop
```

to stop kdm, then

```
sudo /etc/init.d gdm start
```

To start up gdm.

---

### Post by jackwarr on 2008-11-26
I really like Kubuntu and KDM in general, but I've lost the ability to switch between users.  That makes it a bit of a pain as every user must logoff when a new user logs on.  Any idea how I could get around that without reverting to GDM?

---

