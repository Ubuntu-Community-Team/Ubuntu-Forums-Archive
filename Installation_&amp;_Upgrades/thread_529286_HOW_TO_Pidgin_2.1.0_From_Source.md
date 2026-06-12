---
title: "HOW TO: Pidgin 2.1.0 From Source"
date: 2007-08-19
forum: Installation &amp; Upgrades
---

### Post by ryry0666 on 2007-08-19
Installing Pidgin 2.x.x from source is a bit tricky.  When running ./configure, it will stop at errors prompting specific dependencies required.  However, it does not display other "optional" ones that are necessary for all features, such as finch, and SSL support, which is needed for Google Talk.

I made a script that will install all package dependencies as well as compile and install Pidgin.  It can be modified for future versions.  Any improvements to the script will be greatly appreciated.

The script can be downloaded and modified using the following commmands


[LIST=1]
[*]Download the script ```
wget http://www2.ryanaghdam.com/Pidgin.sh
```
[*]Make Executable ```
chmod 711 Pidgin.sh
```
[*]Run Script ```
./Pidgin.sh
```
[/LIST]

---

### Post by Anjue on 2007-08-19
Thanks a lot

---

### Post by jdackle on 2007-08-21
Worked fine for installing Pidgin 2.1.1 on 6.06 Dapper Drake! :)
After I changed the appropriate lines where 2.1.0 was referenced, of course...

I did not however "test" the downloading of Pidgin itself because I'd downloaded it before already, so I commented that line out. But it should pose no problem, I guess.
Just wanted to say it's working. :cool:

Thanks! :)

---

### Post by BooVeMan on 2007-08-21
Hi,
to enable d-bus support you have to add a --enable-dbus to the configure command and install libdbus-1-dev and libdbus-glib-1-dev (the latter I'm not sure if really necessary).
To get documentation you will need to install doxygen and graphviz.

Thanks a lot!

---

### Post by joewalp on 2007-08-23
Saved me considerable time.  Thanks, ryry0666.

---

