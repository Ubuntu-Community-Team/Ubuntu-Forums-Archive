---
title: "sudo apt-get upgrade give me error msg"
date: 2018-10-14
forum: Installation &amp; Upgrades
---

### Post by daveads on 2018-10-14
i tried removing some ppa from software &amp; update....... i did that successfully but i think i might ve tampered with some thing else keep getting this error```
 E: The package code needs to be reinstalled, but I can't find an archive for it. 
```

---

### Post by ajgreeny on 2018-10-14
It is impossible to give you detailed help as we have no idea what that ppa was, nor what package the system can no longer find, so tell us more please.

You may also be able to overcome the problem by enabling the ppa again then using ppa-purge to remove it and restore the standard package that it updated. You will need to install **ppa-purge** to do this.

That ppa-purge package will deal with all the dependencies from the ppa that simply removing the ppa and trying to reinstall a package can not do.

---

### Post by daveads on 2018-10-14
[FONT=arial, sans-serif]Thanks for ur reply
i removed ppa for this application: vlc media player, visual studio code , android studio , and some others 
   // i currently change form windows to linux
so am thinking that this is the course of the errors............ cause am unable to get update from this ppa and i still ve there programs installed probably
or i mistakenly remove something 
                                     [/FONT]

---

### Post by ajgreeny on 2018-10-14
It is very likely that when using the PPAs, many packages as well as the specific ones you wanted (VLC, visual-studio, android-studio, etc) were installed or updated and now there are problems with dependency versions being unfulfilled when you try to update packages.

As I said before you may need to enable the PPAs again and install the packages you had, the use ppa-purge which will remove everything installed from those PPAs cleanly.

---

### Post by daveads on 2018-10-14
alrite i will do just that........... Thanks

from your join Date: july 2005 
// so nice to meet someone who ve been using linux for years...........

---

### Post by solowhigh on 2019-02-10
Try sudo apt-get update?)

---

