---
title: "xgl and beryl problem"
date: 2006-12-05
forum: Installation &amp; Upgrades
---

### Post by loismustdie on 2006-12-05
i'm a new linux user, and i'm loving it, sort of.  i had a heck of a time getting wireless to work (Dell 1390 mini card).  now that it is, i would like to try beryl because i've heard so much about it.

so i'm trying to install beryl and xgl.  but when i go to terminal and do this:

sudo apt-get install xserver-xgl

i get the following error message:

The following packages have unmet dependencies:
  xserver-xgl: Depends: libc6 (>= 2.4-1) but 2.3.6-0ubuntu20 is to be installed
E: Broken packages


what do i need to do?

any help is very, very appreciated.

---

### Post by alpacaman72 on 2006-12-05
I don't know if this will help, but i used the beryl wiki which i would recommend, 
[http://3v1n0.tuxfamily.org/beryl-backup/wiki/Install/Ubuntu/Edgy/XGL](http://3v1n0.tuxfamily.org/beryl-backup/wiki/Install/Ubuntu/Edgy/XGL)
[http://3v1n0.tuxfamily.org/beryl-backup/wiki/Install/Ubuntu/Dapper/XGL](http://3v1n0.tuxfamily.org/beryl-backup/wiki/Install/Ubuntu/Dapper/XGL)
(they recently had a server crash, so these are backups)


to install xgl, try this instead
```
sudo apt-get install xserver-xgl libgl1-mesa xserver-xorg libglitz-glx1 beryl emerald-themes
```

also, are you in dapper or edgy?

---

### Post by loismustdie on 2006-12-05
i'm in 6.06

---

### Post by loismustdie on 2006-12-06
anyone else have any ideas?  what is libc6?  is it something i can download that will satisfay the dependency?  i've gone into synaptic and updated everything and specifically marked that file, but no fix.

please.  help.  please.

---

