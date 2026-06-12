---
title: "Pidgin crashing constantly"
date: 2009-03-04
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by PRGUY85 on 2009-03-04
Hey:

Been using Jaunty alpha for some time now.  However, after the last couple of updates Pidgin has been very crash prone for me.  As I see it, it has something to do with closing messages after being read.  I usually hit Escape key and that's it, the window disappears. Yet now, the window remains as if I just closed a tab inside a window.  Then, Pidgin usually crashes.  I am using Pidgin at the moment without any taskbar icon other than the Indicator applet and the lib-notify plugin for message notifications.  If I don't get any messages at all and leave Pidgin running without performing any actions on it, it remains open without crashes.

Anyone else experiencing this?

---

### Post by Kow on 2009-03-04
Try running pidgin in a terminal and see if it gives and useful debug info. Check the system logs too.

---

### Post by PRGUY85 on 2009-03-04
OK I did that.  Right now the error can be reproduced once I close the message window completely.  If I leave the window open, Pidgin runs fine.  The code given by terminal after crash was:

```
~$ pidgin
Segmentation fault (core dumped)

```

---

### Post by PRGUY85 on 2009-03-04
Anyone?

---

### Post by MacSlow on 2009-03-04
> **PRGUY85 said:**
> Anyone?

Try to runn it like:

```
gdb `which pidgin`
```

Once pidgin crashed go back to the terminal, where you started it from and in the gdb-session there enter:

```
bt
```

followed by <RETURN>. That will hopefully give better clues why and where pidgin crashed for you. Also please don't forget to file a bug against it [here]("https://bugs.edge.launchpad.net/ubuntu/+source/pidgin/+filebug").

Best regards ...

MacSlow

---

### Post by avb on 2009-03-04
probably u have some non standart plugins which is not working good with latest pidgin.

---

### Post by PRGUY85 on 2009-03-04
Only have the following:

Libnotify
History
Nautilus integration

---

### Post by MALEADt on 2009-03-05
> **PRGUY85 said:**
> Only have the following:

Libnotify
History
Nautilus integration

Install -dbg packet of pidgin and its dependencies, and run pidgin under valgrind to check for memory corruption. Check the wiki for some useful pages how to debug crashing applications, and create an bug report :)

---

### Post by Kow on 2009-03-05
> **MALEADt said:**
> Install -dbg packet of pidgin and its dependencies, and run pidgin under valgrind to check for memory corruption. Check the wiki for some useful pages how to debug crashing applications, and create an bug report :)

do the same with gdb too. Without the debug symbols the gdb output would be useless too. Seg faults = accessing memory it shouldn't be. Normally this is an uninitialized variable or one pointing to NULL which means there is a missing sanity check somewhere.

---

