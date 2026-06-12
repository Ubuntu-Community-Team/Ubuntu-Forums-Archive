---
title: "Can't start gdm"
date: 2005-03-17
forum: Installation &amp; Upgrades
---

### Post by krojc on 2005-03-17
My Fault I know...


I uninstalled one packege that I probably should not and now the system cant start gdm, so no x for me.

The error is the error is "/usr/sbin/pmi: no such file or directory, but google returns 0

 I have fortuantelly two machines both installed the same way, with same packages which means that all I have to do is compare the packagelists and install missing. So, 

1. how do I get the list of all installed packages using console and apt?
2. is it possible tu use other package list to comparatively install missing packages?
3. what is the minimal number of package installed to get X working

Thanks in advance. Next time I'll be more careful :)

---

### Post by dusu on 2005-03-17
A way to get the list of packages known by the system is to use
```
dpkg -l
``` 
This will however give you the name of some packages that are not installed... the two  first letters of each line tell you the status of the package. For me, all installed packages are on a line which begin with "ii ", so 
```
dpkg -l | grep '^ii '
``` 
should do the job (I hope !)

---

### Post by krojc on 2005-03-19
Thanks duso. I managed to compare the lista, but what happend is unexplainable...
The package lists are the same, settings the same and I still get an error

can not... S99acpi-something : no such file or directory

The file S99acpi-something is there!! 

and when I start gdm manually i get an error /use/sbin/pmi: no such file or directory.

There really is no such file on the disk, but my other box has no such file either.

I can run xorgcfg and get to X...

Any ideas? Or should I start reinstalling?
Anyhow I need to check how kubuntu looks :)

---

### Post by dusu on 2005-03-19
Sorry but I'm now of no help !
Hope someone else can give you a hand...

---

