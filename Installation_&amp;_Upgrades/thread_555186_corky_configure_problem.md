---
title: "corky configure problem"
date: 2007-09-19
forum: Installation &amp; Upgrades
---

### Post by Hawk__0 on 2007-09-19
hey guys i run ./configure on the source code for corky, and:
```
checking for XDamageQueryExtension in -lXdamage... no
configure: error: Could not find XDamageQueryExtension in -lXdamage
```

i did some googling and didnt find much.. 
i installed the one from synaptic but my friend told me that ones out of date, and he compiled the newest one to install, so i attempted to do the same.  

why am i getting this error?
what do i need in order to compile it?

thanks guys

---

### Post by Pumalite on 2007-09-19
Try this:

sudo apt-get install build-essential

Then try again

---

### Post by Hawk__0 on 2007-09-19
```
build-essential is already the newest version.

```

---

### Post by por100pre1 on 2007-09-19
You can also grab [this]("http://internap.dl.sourceforge.net/sourceforge/conky/conky_1.4.6-1_i386.deb").

---

### Post by Pumalite on 2007-09-19
Pretty good link.

---

### Post by Hawk__0 on 2007-09-19
well i installed it... now i can no longer launch "corky" from command line, and if i try to apti-get it, itsn o longer found (previously the old version would be installed)

---

### Post by chris-man on 2008-01-25
Almost a year late, but in case anyone else is having problems with this, you need to run:
apt-cache search xdamage

---

### Post by enbuyukfener on 2008-04-12
> **chris-man said:**
> Almost a year late, but in case anyone else is having problems with this, you need to run:
apt-cache search xdamage
Thanks :)

Saved me some time.

You may also need the dev files for glib 2.0

For anyone interested:
```
sudo apt-get install libxdamage-dev libglib2.0-dev
```

---

