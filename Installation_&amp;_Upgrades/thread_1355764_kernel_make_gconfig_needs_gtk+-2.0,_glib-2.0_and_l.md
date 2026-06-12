---
title: "kernel make gconfig needs gtk+-2.0, glib-2.0 and libglade-2.0"
date: 2009-12-15
forum: Installation &amp; Upgrades
---

### Post by macstr1k3r on 2009-12-15
I'm trying to compile a custom Linux kernel but I get stuck at "make gconfig", I keep getting this funny error.
```

*
* Unable to find the GTK+ installation. Please make sure that
* the GTK+ 2.0 development package is correctly installed...
* You need gtk+-2.0, glib-2.0 and libglade-2.0.
*
make[1]: *** No rule to make target `scripts/kconfig/.tmp_gtkcheck', needed by `scripts/kconfig/gconf.o'. Stop.
make: *** [gconfig] Error 2

```

---

### Post by lewisforlife on 2009-12-15
Install the following dependencies:


```
sudo apt-get install libgtk2.0-dev libglib2.0-dev libglade2-dev
```

---

### Post by macstr1k3r on 2009-12-15
I get this error:


```
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
```

---

### Post by lewisforlife on 2009-12-15
Do you have Synaptic package manager opened (GUI to install programs).  If you do close it.  If that is not the case you can try:

```
sudo rm /var/lib/apt/lists/lock
```

If you are still getting the lock message, I would try a reboot and that should fix the problem.

---

### Post by macstr1k3r on 2009-12-15
Ok so I type in



and I get this:

```
sudo apt-get install libgtk2.0-dev libglib2.0-dev libglade2-dev
```

```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package libgtk2.0-dev
```

---

### Post by lewisforlife on 2009-12-15
Hmm... libgtk2.0-dev is definitely the name of the library, here is a link to it [http://packages.ubuntu.com/karmic/libgtk2.0-dev](http://packages.ubuntu.com/karmic/libgtk2.0-dev).  Try running the following, then try the install again:

```
sudo apt-get update
```

---

### Post by lewisforlife on 2009-12-15
Also, if you have not already done this, you should install build-essential:

```
sudo apt-get install build-essential
```

---

### Post by macstr1k3r on 2009-12-15
Done the software sources were altered

---

