---
title: "Karmic Alpha 4 - Syncdaemon spawns multiple occurrences"
date: 2009-08-27
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by yellerKat on 2009-08-27
First the client-applet crashes:

/var/crash

> -rw-------  1 xxx  xxx    59903 2009-08-27 12:57 _usr_bin_ubuntuone-client-apple

then this:

```
-rw-------  1 xxx  xxx    21670 2009-08-27 12:59 _usr_lib_ubuntuone-client_ubunt
```

then syncdaemon goes bananas, spawning multiple instances of itself. Anyone else seen similar? I was forced to ctrl-alt-f1 and remove ubuntuone before the machine froze up completely, so I can't provide any further diagnostics.

---

### Post by skeve on 2009-08-28
same here, had to uninstall ubuntuone

---

### Post by camper365 on 2009-08-28
I have that problem too. I posted a thread in the Karmic forums (that you've already seen) and all I need to do when I log in is to run ```
pkill ubuntuone
```
However, that removes use of Ubuntu One so it's not much better than uninstalling it.

---

### Post by mrsurb on 2009-08-28
I had a similar problem - both in Karmic and Jaunty. I just solved it in Jaunty by 'chmod'ing the Ubuntu One folder 777...

---

### Post by yellerKat on 2009-08-28
A couple of python-ubuntuone-xxx updates appear to have fixed the problem for me!

---

### Post by camper365 on 2009-08-28
Updates fixed my problem too

---

