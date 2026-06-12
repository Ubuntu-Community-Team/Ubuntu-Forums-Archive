---
title: "Update Manager broken??"
date: 2009-01-22
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Slug71 on 2009-01-22
Just did some updates a little while ago, first time today, and had some stuff come in for Update Manager, Packagekit, python-apt and maybe some other stuff.
Rebooted and checked for more updates but get this message from update manager:

> Could not initialize the package information

An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Malformed line 68 in source list /etc/apt/sources.list (dist parse)

The Update Manager icon show there are updates. If i try to run;

```
sudo apt-get update
```

I get:
> E:Malformed line 68 in source list /etc/apt/sources.list (dist parse), E:The list of sources could not be read.

??

Have filed a bug.
[https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/320133](https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/320133)

---

### Post by philinux on 2009-01-22
Have you not checked line 68 of your sources list? use gedit and turn on line numbering.

---

### Post by Slug71 on 2009-01-22
Fixed.

My damn Software Sources had Main, Multiverse, Restricted, Universe and Source code all unchecked again.

Rechecked Main, Multiverse, Restricted and Universe and that seemed to do the trick.

---

