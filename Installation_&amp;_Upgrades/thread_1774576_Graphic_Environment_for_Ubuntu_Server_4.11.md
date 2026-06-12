---
title: "Graphic Environment for Ubuntu Server 4.11"
date: 2011-06-03
forum: Installation &amp; Upgrades
---

### Post by rawa on 2011-06-03
Hello

 The 11.04 does Ubuntu Server installed with graphical environment, I'm getting a gnome graphical environment, but I wonder if there are other functional graphical environment with Ubuntu Server, the idea is that it serves to maintain the network and have tools for such end.

 Hear their input, thank you very much.

 Ruben

---

### Post by lykwydchykyn on 2011-06-03
There isn't an official GUI environment designed for server management.  If you must have a GUI and want to save resources, I'd recommend LXDE, install like so:
```

sudo apt-get install xorg lxde lxdm

```

If you're just looking for something GUI-like to manage your system and services, another option is a web-based management tool such as webmin, which you can get from [http://www.webmin.com;](http://www.webmin.com;) or zentyal from [http://www.zentyal.com](http://www.zentyal.com).

---

