---
title: "firefox"
date: 2005-05-15
forum: Installation &amp; Upgrades
---

### Post by [pl]ice on 2005-05-15
hi, i got firefox 1.0.4 .. .gz  un tar move it to /usr/local/share (which path should i install such a programs in? ... )  then run intall, went ok, window opened, then when i close it, and want to run ./firefox nothing happens! just jumps to command line again. not sure what's wrong! i chmod it to my standard user, still the same, when i tried to run ./firefox-bin i get
/firefox-bin: error while loading shared libraries: libmozjs.so: cannot open shared object file: No such file or directory

please advise  ;)

thank you

---

### Post by 23meg on 2005-05-15
[QUOTE='[pl]ice']hi, i got firefox 1.0.4 .. .gz  un tar move it to /usr/local/share (which path should i install such a programs in? ... )  then run intall, went ok, window opened, then when i close it, and want to run ./firefox nothing happens! just jumps to command line again. not sure what's wrong! i chmod it to my standard user, still the same, when i tried to run ./firefox-bin i get
/firefox-bin: error while loading shared libraries: libmozjs.so: cannot open shared object file: No such file or directory

please advise  ;)

thank you[/QUOTE]
 try running it with sudo; is it working? 

warning: just try, don't actually use it!

---

### Post by [pl]ice on 2005-05-16
yes, it does. Didn't think of that... 
  i have changed the owner of all of the firefox files to my standard but it doesn't help, still have to use sudo, can u please tell me how to adjust that? and what is the reason for that behaviour?

thank you.

---

### Post by kiddyfurby on 2005-05-16
I overwrited my default firefox with 1.0.4, works perfectly
there is also firefox 1.0.4 in backports

---

