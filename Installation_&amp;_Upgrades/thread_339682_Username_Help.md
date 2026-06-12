---
title: "Username Help"
date: 2007-01-16
forum: Installation &amp; Upgrades
---

### Post by floyd.lt on 2007-01-16
I just installed Xubuntu on my old computer using the Alternate Xubuntu 6.10 i386 CD.
Everything went fine except i couldn't set up my username during the install. I could just set up the password and now i don't know what's the username. Maybe xubuntu has a default username?

---

### Post by wpshooter on 2007-01-16
Are you sure that you did install either a server install or an OEM install instead of a DESKTOP/workstation install ?

---

### Post by taurus on 2007-01-16
Your login name is oem and the password is the one that you created during the installing process.  Once you log in, open a terminal and run

```
sudo oem-config-prepare
```
That will create a regular account for you to use from now on and remove the oem at the same time.

p.s.  I guess somehow you decided to pick the second option, oem install, at the first screen because the first option would allow you to do a normal install.

---

