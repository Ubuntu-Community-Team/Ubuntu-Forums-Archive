---
title: "Update manager errors"
date: 2009-12-11
forum: Installation &amp; Upgrades
---

### Post by newbeeman on 2009-12-11
I have just upgraded to 9.1 successfully until I tried to check for updates and ran into a problem with the manager.

The error reads 
"Could not initialize the package information"
An unresolvable problem occurred while initializing the package information.
Please report this bug against the 'update-manager' package and include the following error message:
'E:Malformed line 32 in source list /etc/apt/sources.list (dist parse), E:The list of sources could not be read.'

Could someone please explain what this means and how to correct the error?  Where, when and how to report the error?

---

### Post by MelDJ on 2009-12-11
could you post your sources list?

---

### Post by newbeeman on 2009-12-11
I will do my best here is a screenshot. I did manage to download some updates but still with errors

---

### Post by MelDJ on 2009-12-11
type this in terminal and post the output : gedit /etc/apt/sources.list

---

### Post by newbeeman on 2009-12-11
Tried that got a 'no such file'.

---

### Post by MelDJ on 2009-12-11
it seems that you sources list is unreadable/deleted.
i don't know how to fix it. but you could try reporting at launchpad

---

### Post by newbeeman on 2009-12-11
OK will do.

---

