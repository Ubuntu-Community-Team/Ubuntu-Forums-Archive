---
title: "disabling X"
date: 2008-01-31
forum: Installation &amp; Upgrades
---

### Post by evymetal on 2008-01-31
Hi,
I've just installed two machines but accidentally installed it with X, gnome etc. What's the best way to make it boot up without any display manager (ie straight into console, I'm going to use ssh to get in, and they're headless - so having a display manager is a bit pointless)

---

### Post by evymetal on 2008-01-31
Ah, found it:

sudo apt-get install  sysv-rc-conf

sudo  sysv-rc-conf

---

### Post by phatchow on 2008-01-31
apt-get remove xdm

Then X won't start when the machine boots.  You could of course uninstall xorg, etc. but what I suggested would be easiest.

---

### Post by evymetal on 2008-02-02
thanks

---

