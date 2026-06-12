---
title: "Installation no GUI"
date: 2008-10-06
forum: Installation &amp; Upgrades
---

### Post by jcsambo on 2008-10-06
I installed the Ubuntu from the disc I received. Installation was complete. After boot up the computer now asking for a username and password in console mode. like cmd in windows.

please help.

---

### Post by Partyboi2 on 2008-10-06
Are you trying to install the Desktop version or the server version of ubuntu?

---

### Post by zvacet on 2008-10-07
If you installed desktop version then login and type this

```
startx
```

or 

```
sudo /etc/init.d/gdm start
```

If you installed server version then 

```
sudo apt-get install ubuntu-desktop
```

---

