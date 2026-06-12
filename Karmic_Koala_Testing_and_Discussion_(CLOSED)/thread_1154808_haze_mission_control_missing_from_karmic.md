---
title: "haze mission control missing from karmic"
date: 2009-05-10
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by puccaso on 2009-05-10
all this news about empathy being included in gnome... until the "network error" goof is fixed, we need the haze mission control included in karmic.

---

### Post by olskar on 2009-05-10
> **puccaso said:**
> all this news about empathy being included in gnome... until the "network error" goof is fixed, we need the haze mission control included in karmic.

What is it?

---

### Post by puccaso on 2009-05-10
its an alternative msn connectino manager thingi for empathy...

---

### Post by super.rad on 2009-05-10
do you mean telepathy-haze? if so it's already included

---

### Post by taavikko on 2009-05-10
> **super.rad said:**
> do you mean telepathy-haze? if so it's already included

Yes:
```
aptitude show telepathy-haze 
Package: telepathy-haze
State: installed
Automatically installed: yes
Version: 0.3.0-1

```

installing empathy brings it in.

There isn't any talks replacing pidgin with empathy yet.
If somebody brings it up in UDS, then we'll know

---

### Post by puccaso on 2009-05-10
if the correct thing was installed
in empathy, you would see two different MSN protocols when trying setup an msn account..

---

### Post by super.rad on 2009-05-10
```
ben@ben-desktop:~$ sudo aptitude show telepathy-haze
Package: telepathy-haze
State: installed
Automatically installed: no
Version: 0.3.0-1
Priority: optional
Section: universe/net
Maintainer: Ubuntu MOTU Developers <ubuntu-motu@lists.ubuntu.com>
Uncompressed Size: 201k
Depends: libc6 (>= 2.4), libdbus-glib-1-2 (>= 0.78), libglib2.0-0 (>= 2.16.0),
         libpurple0 (>= 1:2.5.5-1ubuntu8), libtelepathy-glib0 (>= 0.7.21)
Provides: telepathy-connection-manager
Description: A telepathy connection manager that use libpurple
 Haze is a telepathy connection manager based on libpurple. This allow telepathy
 based application to connect all protocols supported by libpurple (pidgin).

ben@ben-desktop:~$ sudo aptitude show telepathy-butterfly
Package: telepathy-butterfly
State: installed
Automatically installed: yes
Version: 0.3.3-2
Priority: optional
Section: universe/net
Maintainer: Ubuntu MOTU Developers <ubuntu-motu@lists.ubuntu.com>
Uncompressed Size: 225k
Depends: python (>= 2.4), python-central (>= 0.6.11), python-dbus,
         python-gobject, python-telepathy (>= 0.15.6), python (>= 2.5) |
         python-ctypes, python-msn (>= 0.3.0)
Provides: telepathy-connection-manager
Description: MSN connection manager for telepathy
 MSN connection manager for telepathy that handles presence, personal messages,
 conversations, avatars and groups.
```
It is telepathy-haze you were on about, I have both installed but only have 1 msn protocol shown when setting up an account but there is an option to import accounts which finds my msn account from pidgin

---

### Post by SKLP on 2009-05-11
It seems MSN(Haze) only becomes visible if one uninstalls telepathy-butterfly

---

