---
title: "wine not allowing me to browse"
date: 2008-09-24
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by cykotiktek on 2008-09-24
I did the upgrade to intrepid ibex and since then i have not been able to browse the wine C:  When i try to run a program out of wine it will say ... starting ventrillo on the task bar and then it will disapear.  I have uninstalled wine and reinstalled it and same thing.  Any other suggestions?

---

### Post by zoomy942 on 2008-09-24
its doing that to me too

---

### Post by BwackNinja on 2008-09-24
Run in terminal and report the output. Wine of all programs always says something at least half-useful when it crashes.

---

### Post by cykotiktek on 2008-09-24
wine: could not load L"C:\\windows\\system32\\PROGRAM.exe": Module not found


Is what i am getting when i run it in terminal.

---

### Post by BwackNinja on 2008-09-24
I'd say that's something an uninstall and reinstall wouldn't fix. Delete or rename your .wine, and make a new one. Something must be out of date there. Check if that file "C:\\windows\\system32\\PROGRAM.exe" exists in ~/.wine/drive_c/windows/system32/PROGRAM.exe. Alternatively, running winecfg might magically fix stuff.

---

