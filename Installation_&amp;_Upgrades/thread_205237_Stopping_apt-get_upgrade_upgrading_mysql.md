---
title: "Stopping apt-get upgrade upgrading mysql"
date: 2006-06-28
forum: Installation &amp; Upgrades
---

### Post by grahamdoel on 2006-06-28
I have been using a package that is incompatible with mysql 5.  Every time I run apt-get upgrade it upgrades mysql and breaks my library.

Can anyone tell me how to (or where to find out how to) stop apt-get upgrade upgrading mysql, but upgrading everything else?

Thanks

---

### Post by bikeboy on 2006-06-28
Can't remember exactly how, but it can be done through aptitude and the effects will be included in apt-get (ie. it will keep the current version).

If you're running with a gui open up Synaptic, select the package, click the "Package" menu and then "Lock Version". Again apt-get will obey this lock.

---

### Post by grahamdoel on 2006-06-28
Thank you, though. I'm not running a GUI, any other suggestions?  Though eaching for "lock version" should produce some more helpful results.

---

### Post by bikeboy on 2006-06-28
Seem to have worked out how to do it in aptitude.```
sudo aptitude
``` Make your way to the package, "?" to get help navigating. Once you're on it press the = sign, this will place a "hold" on that package as indicated by the letter "h" appearing next to its name.

edit: In fact you can simply do "sudo aptitude hold <packagename>"

---

### Post by grahamdoel on 2006-06-28
thanks Bikeboy that is just the job.

I also found out how to do it via the cli

> echo "[PACKAGE] hold" | dpkg --set-selections

but I'll stick with aptitude

---

