---
title: "Firefox still 1.5! [Resolved]"
date: 2007-03-17
forum: Installation &amp; Upgrades
---

### Post by davidandrew52 on 2007-03-17
I have upgraded firefox a couple of times but when I open it it is still version 1.5.  Synaptic and apt both tell me that I have 2.0.0.2 installed but when I open either from a menu or from a terminal the same thing happens.  I have reinstalled it.

Short of removing it and reinstalling is there anything I can do?

---

### Post by aysiu on 2007-03-17
Are you using Dapper Drake (6.06) or Edgy Eft (6.10)?

And did you ever install Firefox in a different way from Synaptic/apt? Say, Automatix or some other script? Or instructions from the Wiki?

---

### Post by davidandrew52 on 2007-03-17
I am using 6.10 - I upgraded to 6.10 and Firefox 2 using the Update manager.  I did once use Automatix but that was before I upgraded to 6.10.

---

### Post by aysiu on 2007-03-17
Can you post the output of these terminal commands? ```
cd /opt
ls
cd firefox
ls
```

---

### Post by jackrobinson on 2007-03-17
> **davidandrew52 said:**
>  I did once use Automatix but that was before I upgraded to 6.10.
to do what?

---

### Post by davidandrew52 on 2007-03-18
> **aysiu said:**
> Can you post the output of these terminal commands? ```
cd /opt
ls
cd firefox
ls
```

cd /opt
ls
firefox
cd firefox
ls
chrome                    libnssckbi.so       mozilla-xremote-client
components                libplc4.so          plugins
defaults                  libplds4.so         readme.txt
extensions                libsmime3.so        removed-files
firefox                   libsoftokn3.chk     res
firefox-bin               libsoftokn3.so      run-mozilla.sh
greprefs                  libssl3.so          searchplugins
icons                     libxpcom_compat.so  updater
libmozjs.so               libxpcom_core.so    updater.ini
libnspr4.so               libxpcom.so         xpicleanup

---

### Post by yabbadabbadont on 2007-03-18
```
cd /opt
sudo rm -rf firefox
```
Make darn sure you type that correctly...

---

### Post by davidandrew52 on 2007-03-18
When I try and start firefox  I now get a message:
Failed to execute child process "firefox" (No such file or directory)

---

### Post by yabbadabbadont on 2007-03-18
Force the firefox from the repositories to be reinstalled using synaptic.

---

### Post by aysiu on 2007-03-18
> **yabbadabbadont said:**
> Force the firefox from the repositories to be reinstalled using synaptic.
Actually, you're missing a step.

You need to not only remove the new Firefox but also remove the symlink to its launcher: ```
sudo rm /usr/bin/firefox
sudo dpkg-divert --rename --remove /usr/bin/firefox
sudo rm /usr/bin/mozilla-firefox
sudo dpkg-divert --rename --remove /usr/bin/mozilla-firefox
```

---

### Post by davidandrew52 on 2007-03-18
Thanks thats done it.

Thanks everyone!:)

---

