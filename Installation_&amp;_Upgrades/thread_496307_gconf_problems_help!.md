---
title: "gconf problems help!"
date: 2007-07-09
forum: Installation &amp; Upgrades
---

### Post by erwinquita on 2007-07-09
I'm having problems logging in after upgrading from gaim to pidgin my I think my gconf files have been messed up... and here's the xsession log. Any help would be appreciated.

```

/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/X11R6/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "username"
/etc/gdm/Xsession: Beginning session setup...
/etc/profile: 20: [[: not found
GConf Error: Adding client to server's list failed, CORBA error: IDL:omg.org/CORBA/COMM_FAILURE:1.0
GConf Error: Adding client to server's list failed, CORBA error: IDL:omg.org/CORBA/COMM_FAILURE:1.0
No such file `/usr/lib/libgconf2-4/2/libgconfbackend-xml.so'

No such file `/usr/lib/libgconf2-4/2/libgconfbackend-xml.so'

No such file `/usr/lib/libgconf2-4/2/libgconfbackend-xml.so'

No such file `/usr/lib/libgconf2-4/2/libgconfbackend-xml.so'

No such file `/usr/lib/libgconf2-4/2/libgconfbackend-xml.so'

No such file `/usr/lib/libgconf2-4/2/libgconfbackend-xml.so'

No such file `/usr/lib/libgconf2-4/2/libgconfbackend-xml.so'

gconf-sanity-check-2 did not pass, logging back out

```

---

### Post by r0ck80y on 2007-07-09
delete .dmrc, .gconf/ .gconfd/ and .xsession-errors from your home folder and login again.

---

### Post by erwinquita on 2007-07-12
Rock,

It did not work! Oh I'm so close to formating my hard disk.... anyone please help!

---

