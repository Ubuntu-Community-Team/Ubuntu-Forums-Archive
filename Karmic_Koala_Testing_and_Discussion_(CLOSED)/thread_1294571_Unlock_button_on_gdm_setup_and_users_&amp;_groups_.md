---
title: "Unlock button on gdm setup and users &amp; groups doesn't work"
date: 2009-10-18
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by benerivo on 2009-10-18
When i go to *System>Administration>Login Window* or *System>Administration> Users and Groups* the unlock button does nothing. I can run the Users and Groups with gksudo which bypasses the unlock function, but gksudo has no effect for the gdm configuration. Does anyone no where there is a file that I can change to allow me to autologin - which is really all i want to do.

---

### Post by zika on 2009-10-18
> **benerivo said:**
> When i go to *System>Administration>Login Window* or *System>Administration> Users and Groups* the unlock button does nothing. I can run the Users and Groups with gksudo which bypasses the unlock function, but gksudo has no effect for the gdm configuration. Does anyone no where there is a file that I can change to allow me to autologin - which is really all i want to do.
```
$ cat /etc/gdm/custom.conf
[daemon]
TimedLoginEnable=false
AutomaticLoginEnable=true
TimedLogin=user_You_want_to_login
AutomaticLogin=user_You_want_to_login
TimedLoginDelay=30
```
```
sudo nano /etc/gdm/custom.conf
``` and make it look like the one above.

---

### Post by benerivo on 2009-10-19
thanks

---

