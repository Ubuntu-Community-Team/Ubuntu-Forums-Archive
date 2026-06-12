---
title: "libc6 problem after ubuntu mate upgrade to 21.04"
date: 2021-07-09
forum: Installation &amp; Upgrades
---

### Post by strolego on 2021-07-09
I have updated ubuntu from 20.10 to 21.04

apt says that the version of  package libc6 is 2.33, but in folder
*/usr/lib/x86_64-linux-gnu/*  there is only libc-2.32.so.

I have tried to reinstall with apt, then manually with dpkg but I
obtained no results.

The problem is that some programs do not work (i.e. R) because they
explicitely request version 2.33 of libc6.

What can I do?

---

### Post by Impavidus on 2021-07-09
You should have 2.33. Let's run a few checks:```
dpkg-query --listfiles libc6 | grep libc
apt-cache policy libc6
```

---

### Post by strolego on 2021-07-09
> **Impavidus said:**
> You should have 2.33. Let's run a few checks:```
dpkg-query --listfiles libc6 | grep libc
apt-cache policy libc6
```

output of dpkg-query --listfiles libc6 | grep libc

```
/lib/x86_64-linux-gnu/libc-2.33.so/usr/share/doc/libc6
/usr/share/doc/libc6/NEWS.Debian.gz
/usr/share/doc/libc6/NEWS.gz
/usr/share/doc/libc6/README.Debian.gz
/usr/share/doc/libc6/README.hesiod.gz
/usr/share/doc/libc6/changelog.Debian.gz
/usr/share/doc/libc6/copyright
/usr/share/lintian/overrides/libc6
/lib/x86_64-linux-gnu/libc.so.6
```

but i have also this output for
ls -l  /usr/lib/x86_64-linux-gnu/libc.so*

```
-rw-r--r-- 1 root root 298 mar 31 15:44 /usr/lib/x86_64-linux-gnu/libc.solrwxrwxrwx 1 root root  12 dic 19  2020 /usr/lib/x86_64-linux-gnu/libc.so.6 -> libc-2.32.so

```

i.e. I have libc6 2.32 in /usr/lib/  AND libc6 2.33 in /lib

---

### Post by monkeybrain20122 on 2021-07-09
libc.so.6 is a symbolic link and it is currently linked to libc-2.32.so, that means libc-2.32.so is somehow in your system, either because upgrade wasn't done properly and left junks around (I always prefer clean install as oppose to "upgrade") or you have installed some third party software (via sudo make install) either in your old system (so upgrade didn't remove it) or in the new system.

---

### Post by Impavidus on 2021-07-10
On Ubuntu /lib is nowadays a symlink to /usr/lib. Is it on your system too? Your output from **dpkg-query --listfiles libc6 | grep libc** appears normal. Your output from **ls -l  /usr/lib/x86_64-linux-gnu/libc.so*** is almost normal, except that that symlink should point to libc-2.33.so, not to libc-2.32.so. Does this file (libc-2.32.so) exist or is it a dangling link? If the file exists, you have both 2.32 and 2.33 installed and are using 2.32 as default.

---

### Post by strolego on 2021-07-10
There was a problem with usrmerge in  the upgrade and not all the files in /lib are symlink to /usr/lib. I'm trying to recover bya
 hand

---

### Post by monkeybrain20122 on 2021-07-10
> **strolego said:**
> There was a problem with usrmerge in  the upgrade and not all the files in /lib are symlink to /usr/lib. I'm trying to recover bya
 hand

In that case your libc6 problem is probably just the tip of the iceberg, you may be able to fix this one problem manually but you won't be able to fix or even detect all of them, some of that may manifest later as hard to diagnose problems. One day your system may behave strangely or some software doesn't run because your libs are all mixed up and nobody knows why. 

Maybe I am kind of OCD, but to my mind the fact that this happens as a result of a glitch in "upgrade" is a sign that this system cannot be trusted to operate properly. If I were you I would do a backup of my data, wipe everything clean and do a fresh install.

---

