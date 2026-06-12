---
title: "AWN icons don't draw properly in Ibex"
date: 2008-10-04
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by the real omni on 2008-10-04
Having updated from 8.04 to 8.10 alpha 6, the icons in my AWN dock don't draw properly.

In hardy I was using the -trunk version of Avant Window Navigator but it didn't work in 8.10 so I switched to the normal (non -trunk) version. 

Now, sometimes the icons draw properly but sometimes they have a grey line beside them, as illustrated in the attached screenshot.

Anyone know why, and how to fix it? :)

---

### Post by stewacide on 2008-10-04
I noticed this as well.

---

### Post by tghe-retford on 2008-10-04
This looks similar to the problem I had with QT applications. I tested AWN on my computer after I downgraded the NVidia restricted drivers from version 177 to version 173 for another problem (you can do this via the Hardware Drivers option in the administration option) and it looks fine - no problems with icons as your screenshot shows.

See also: [http://ubuntuforums.org/showthread.php?t=938149](http://ubuntuforums.org/showthread.php?t=938149)

---

### Post by the real omni on 2008-10-04
Update:

I just tried uninstalling awn and re-installing the -trunk version since there've been HEAPS of updates to Intrepid over the past 2 days..

Having switched back to the -trunk version, the icon-drawing bug seems to have gone away.

To switch to the -trunk version, just go into synaptic package manager and uninstall everything matching 'avant' and install everything matching 'avant*trunk'

---

### Post by the real omni on 2008-10-04
Update: 

Seems I was wrong - the icons still draw incorrectly now and then even with the -trunk version.

One thing to note, though, is it only seems to happen with the applets, not with the launchers.

---

