---
title: "xsession errors"
date: 2005-04-08
forum: Installation &amp; Upgrades
---

### Post by brickbat on 2005-04-08
i found this hidden file in my home directory.  it has many things in it but this line is repeated the most.

** (gnome-cups-icon:9415): WARNING **: failed request with status 1030

also mail notifier was working fine and then just stopped.
this error is in the same file

mail-notification: ath.c:181: _gcry_ath_mutex_lock: Assertion `*lock == ((ath_mutex_t) 0)' failed.

i did a google search with no luch.

suggestions please?

ciao,
bb

---

### Post by ubuntu_demon on 2005-04-09
[QUOTE=brickbat]i found this hidden file in my home directory.  it has many things in it but this line is repeated the most.

** (gnome-cups-icon:9415): WARNING **: failed request with status 1030

also mail notifier was working fine and then just stopped.
this error is in the same file

mail-notification: ath.c:181: _gcry_ath_mutex_lock: Assertion `*lock == ((ath_mutex_t) 0)' failed.

i did a google search with no luch.

suggestions please?

ciao,
bb[/QUOTE]
 try :
sudo apt-get update
sudo apt-get install ubuntu-base ubuntu-desktop
sudo apt-get dist-upgrade

---

