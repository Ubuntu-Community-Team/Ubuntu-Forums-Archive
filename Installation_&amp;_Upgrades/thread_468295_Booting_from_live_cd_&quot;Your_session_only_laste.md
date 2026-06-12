---
title: "Booting from live cd: &quot;Your session only lasted less than 10 secconds...&quot;"
date: 2007-06-08
forum: Installation &amp; Upgrades
---

### Post by jew on 2007-06-08
I'm trying to install ubuntu on a spare computer here and every time i boot from the live cd i'm getting the "Your session only lasted less than 10 secconds..." error and the details show this:

/etc/gdm/PreSession/Default: Registering your session with wtmp and utemp
/etc/gdm/PreSession/Default: running: /usr/X11R6/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "ubuntu"
/etc/gdm/Xsession: Beginning session setup...
/usr/bin/ssh-agent: error while loading shared libraries: /usr/lib/libgssapi_krb5.so.2: invalid ELF header


this is with the 7.04 cd. this computer has 3 hard drives hooked up and all of them have over 10gb of free space.

---

### Post by merlinus on 2007-06-08
Did you check the cd for errors?  

Also, burning it at a slow speed (4x) is a good idea.

-merlin

---

### Post by jew on 2007-06-10
yeah there was an error on it, i'm going to try burning it again slower.

---

### Post by jew on 2007-06-10
it worked after reburning. i'll try to make sure i check things like that before i post noob questions again :)

---

### Post by merlinus on 2007-06-10
No problem -- that's why we are here.

Glad it worked!

-merlin

---

