---
title: "sources list"
date: 2007-10-01
forum: Installation &amp; Upgrades
---

### Post by gidrdunv11 on 2007-10-01
Any ideas how to resolve this one

A unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Type 'sudo' is not known on line 45 in source list /etc/apt/sources.list, E:The list of sources could not be read.'

---

### Post by trippinnik on 2007-10-02
type:
gksudo gedit /etc/apt/sources.list
type your password
find the offending line and remove sudo (or comment it out wth #)

---

### Post by Seisen on 2007-10-02
You can also post your source list and we can help you find the bad line in your source list.

---

### Post by Sef on 2007-10-02
> 'E:Type 'sudo' is not known on line 45 in source list /etc/apt/sources.list, E:The list of sources could not be read.'

Line 45 is the problem.  Put a # in front of it.   The # tells the machine to ignore that line.

---

### Post by gidrdunv11 on 2007-10-02
Thanks, I'm a little slow on the uptake with this do it yourself stuff. Still a bit of a Windowp.

---

