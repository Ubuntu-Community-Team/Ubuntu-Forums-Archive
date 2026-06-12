---
title: "Cant Run Opera"
date: 2007-06-11
forum: Installation &amp; Upgrades
---

### Post by Cam1223 on 2007-06-11
I downloaded the .deb file and did ```
dpkg -i --force-architecture
``` but when i try to start opera the terminal spits this out
```
ERROR: ld.so: object 'libjvm.so' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object 'libawt.so' from LD_PRELOAD cannot be preloaded: ignored.
/usr/lib/opera/9.21-20070510.6/opera: error while loading shared libraries: libqt-mt.so.3: wrong ELF class: ELFCLASS64

```

seems like it has something to do with the program being 32bit and me being on a 64bit but i have heard people say it worked for them. plz help i really dont like firefox!

---

### Post by kerry_s on 2007-06-11
no you just didn't install the dependency,s. open synaptic click on opera an select fix broken from the menus above or from command line> sudo apt-get -f install

---

### Post by Cam1223 on 2007-06-12
ok i fixed it, it wasent the dependancies it was that i had to use the static .deb that they had. it still says that error but it runs now

---

### Post by kerry_s on 2007-06-12
yeah you could do that to, but static has crappy fonts and some things are disabled.

here's the dependency's,if you install the 4, the regular opera will work, see pic->

---

### Post by Cam1223 on 2007-06-12
true it does look a little weird from the windows version i have on xp but the problem was that it dosent say opera in synaptic and the command for the terminal did nothing i think it said sumthing like it couldent find anything. atleast it runs now but gnome keeps poppin up firefox windows i already changed it in prefferd aplications but it keeps doing it. i guess thats why i had to go in the config to turn on speeddial

---

### Post by kerry_s on 2007-06-12
when you use dpkg -i to install it, it will show in synaptic as a broken package, click on it to highlight it, then click> edit > fix broken package and it will install the missing dependencys.

remove the static version before you try the regular one again, click on status> installed to find the opera you got now, right click it and mark for complete removal.

---

### Post by Joseaa on 2007-06-13
> **kerry_s said:**
> yeah you could do that to, but static has crappy fonts and some things are disabled.

here's the dependency's,if you install the 4, the regular opera will work, see pic->

Opera has not released 64 bit version yet. So, only static version can run 64 bit architecture.

---

