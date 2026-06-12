---
title: "ubuntu CD  boot -- &quot;Starting GNOME Display Manager&quot;"
date: 2007-08-03
forum: Installation &amp; Upgrades
---

### Post by ssachida on 2007-08-03
Hi,

I'm trying to install Ubuntu (7.04) with the install CD. I have checked that the CD is ok (md5sum of ISO, and Check CD from the menu).

The ubuntu boot stops at "Starting GNOME Display Manager". The machine is a Dell Precision 490 with 2  dual core Intel Xeons. The graphics driver is Nvidia GeForce.

Alt+Ctrl+F1 takes me to the console and i can execute pretty much anything with sudo.

So...
1. How do I get Gnome started up
2. how do I do the install from the command line?

---

### Post by buckrodgers on 2007-08-13
I do not know how it works on the live CD but you can get the alternate CD designed for comand line install

cheers

---

### Post by merlinus on 2007-08-13
You might try this:
```

sudo dpkg-reconfigure xserver-xorg

```
You can probably go with the default for most screens, but select "vesa" for your video driver.

Then:
```

startx

```
-merlin

---

### Post by adityabheemarao on 2007-09-08
goto  Alt+Ctrl+F5  
login on command line

Try:

```

sudo rm /tmp/.X0-lock

```

And then:
```

startx

```

if the problem is due to the login manager, this will bypass it.

---

