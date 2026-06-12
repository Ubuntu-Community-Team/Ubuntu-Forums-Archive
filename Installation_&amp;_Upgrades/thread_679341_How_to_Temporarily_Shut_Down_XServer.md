---
title: "How to Temporarily Shut Down XServer"
date: 2008-01-26
forum: Installation &amp; Upgrades
---

### Post by mdintzis on 2008-01-26
There's a certain system command whose syntax differs from one distribution to another, and I'm trying to find out what it is in Ubuntu.

The command I'm searching for is the one that you use to temporarily exit the XServer environment in order to install a different video driver or change driver settings.

In Mandriva, it is "Init 3".
In RedHat, it is "/sbin/Init 3"

Could someone please tell me what the correct command syntax is in Debian/Ubuntu?

Thanks.

---

### Post by taurus on 2008-01-26
Press <Ctrl><Alt>F2 and login with your name and password.  Then, stop the X server with

```
sudo /etc/init.d/gdm stop
```
If you want to start it again, just run

```
sudo /etc/init.d/gdm start
```

---

