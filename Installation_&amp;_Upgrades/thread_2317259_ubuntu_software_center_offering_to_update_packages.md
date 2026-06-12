---
title: "ubuntu software center offering to update packages I don't have"
date: 2016-03-14
forum: Installation &amp; Upgrades
---

### Post by Malik_Rumi on 2016-03-14
I do not have and have never had on this machine mysql. But the updater is constantly offering me a mysql update. There is no obvious way to stop this, so I am posting to ask how to do that. Thanks

---

### Post by QIII on 2016-03-14
Could you please post the results of 

```
which mysql
```

---

### Post by mastablasta on 2016-03-15
sometimes applications use databases and some use MySQL.

---

### Post by Malik_Rumi on 2016-03-16
/usr/bin/mysql

So I guess it has been lurking there in the background as a pre-installed app that I never looked for because I never wanted it. But at least now I know. Is there such a thing as a list of all default / included / pre-installed programs?

Thanks.

---

### Post by ian-weisser on 2016-03-17
Such a list would be very long, and not useful.
'Pre-installed programs' would include hundreds of shell commands, dbus services, compilers and intepreters, each of which is a separate program. Probably not what you seek.


If you want to see what you have installed that uses mysql, simply simulate uninstalling mysql.
```
apt-get remove --simulate mysql
```

If you want to see what desktop applications are installed by default, you can get an approximation by looking at the desktop metapackage dependencies. This is top-level only, not a complete list. 
```
apt-cache depends ubuntu-desktop
```

---

### Post by Malik_Rumi on 2016-03-17
Thanks! There's always something new to learn.

---

