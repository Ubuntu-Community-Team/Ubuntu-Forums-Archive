---
title: "Fingerprint GUI not working in 11.10"
date: 2011-10-22
forum: Installation &amp; Upgrades
---

### Post by mynameissagarbhatt on 2011-10-22
After upgrade fingerprint GUI doesn't seem to work during logon......however, i am able use it once the system is on( like unlocking locked screen),,,,,,any clue?

---

### Post by kombipom on 2011-10-24
I think it's because the login manager changed from gdm to lightdm (or something like that).  I'm looking for a way to switch it back or enable fingerprint gui in lightdm.

---

### Post by kombipom on 2011-10-24
To switch back to gdm (which re-enables fingerprint log in):

Open Terminal
Type : ```
sudo dpkg-reconfigure gdm
```

Hit enter for OK
Select gdm
Restart

---

### Post by mynameissagarbhatt on 2011-10-27
It worked! thnx man..

---

