---
title: "GRAMPS Not Opening With Lucid Apha 2 (Kubuntu)"
date: 2010-01-25
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by zenarcher on 2010-01-25
I installed GRAMPS in Lucid Alpha 2, using Synaptic Package Manager.  The first time I attempted to start GRAMPS, it failed to open and I receive the following error message:

2384: ERROR: gramps.py: line 215: Gramps failed to start.
Traceback (most recent call last):
  File "/usr/share/gramps/gramps.py", line 193, in run
    gramps_main.Gramps(args)
  File "/usr/share/gramps/gramps_main.py", line 236, in __init__
    self.vm = ViewManager.ViewManager(state)
  File "/usr/share/gramps/ViewManager.py", line 231, in __init__
    self.__build_main_window()
  File "/usr/share/gramps/ViewManager.py", line 278, in __build_main_window
    self.uimanager, self.progress_monitor, self)
  File "/usr/share/gramps/DisplayState.py", line 324, in __init__
    self.last_bar = self.status.insert(min_width=15, ralign=True)
  File "/usr/share/gramps/widgets/statusbar.py", line 167, in insert
    label.set_alignment(xalign=1.0, yalign=0.5)
AttributeError: 'gtk.HBox' object has no attribute 'set_alignment'

I have filed a Bug Report on the problem (Bug 512241).  If anyone else is experiencing the issue, you might want to add to the bug report.

Thanks,
zenarcher

---

### Post by SevenMachines on 2010-01-25
i think its something that changed in gtk 2.19, the fix is in gramps svn

---

### Post by zenarcher on 2010-01-27
Well, the fix worked perfectly!  Thanks so much for the efforts!

Cheers,
zenarcher

---

### Post by SevenMachines on 2010-01-27
Glad it works, be nice to get as many universe packages working as possible, at least peoples favourites :) Plenty of time for more bug fixing after autosyncing freeze in a few weeks too!

---

