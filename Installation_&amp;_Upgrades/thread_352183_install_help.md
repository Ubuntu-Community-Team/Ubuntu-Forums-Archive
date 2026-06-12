---
title: "install help"
date: 2007-02-03
forum: Installation &amp; Upgrades
---

### Post by benner on 2007-02-03
i have an older machine that i have been noodling around with to test out linux and learn everythingi can.  currently, it is so gummed up with stuff, i am ready to wipe it and start fresh.  i started with edubuntu (dapper) and upgraded to edgy, installed kde, xfce, language support for a million languages, every program for everything i could think of.  now, it is starting to freeze up and there are all kinds of little quirks.

i have settled on xubuntu and am ready to wipe everything and start fresh.  problem is, i want to do it today.  i don't have a copy of the cd here, the linux box has no burner and  my other computer has a broken burner.  i figure that there must be some simple apt-get  that will alow me to do this online.   suggestions?  

thanks in advance for any help.

---

### Post by moffa on 2007-02-03
Try ```
 sudo aptitude update && sudo aptitude install xubuntu-desktop 
```

That should install xubuntu desktop (uses less memory).  After everything is installed you can remove ubuntu (gnome) packages.  Haven't tried it myself, but it should work.

---

