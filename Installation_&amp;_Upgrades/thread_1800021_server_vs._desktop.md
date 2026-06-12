---
title: "server vs. desktop"
date: 2011-07-08
forum: Installation &amp; Upgrades
---

### Post by Skaperen on 2011-07-08
Is there any difference between the packages in the repository, for ubuntu-XXX-server vs. ubuntu-XXX-desktop vs. kubuntu-XXX-desktop?  Or are the different systems based just on what the default install from the ISOs is?

---

### Post by IWantFroyo on 2011-07-08
It's just the default install, plus different apps. Server is more spartan. Desktop has all sorts of apps scattered through it.

---

### Post by Skaperen on 2011-07-08
> **IWantFroyo said:**
> It's just the default install, plus different apps. Server is more spartan. Desktop has all sorts of apps scattered through it.

OK, so information I get about packages available for a specific version (example 10.04.2 LTS or maybe 11.04) and architecture (amd64 vs. i386) would be the same no matter what class (e.g. -desktop vs -server, ubuntu vs. kubuntu) I do this under?  I do know I can do things like install KDE onto ubuntu and make it like kubuntu.  I could not tell if this also applied for -server without actually installing every ubuntu system class and doing "aptitude show" and "apt-cache dump" everywhere and comparing.

There is a different kernel for -server, but it is clearly named with -server in the name.  Presumably someone morphing a server install into a desktop install would change the kernel package over, too.  Someday I may even try that (after doing a package list diff between a pristine server install and a pristine desktop install and doing install and purge to apply that difference).

---

### Post by ajgreeny on 2011-07-08
The repositories available are exactly the same and completely independent of the version of ubuntu (or kubuntu, or xubuntu, etc etc) that you start from.

In effect that means you can turn anything into anything else; as you suggest you can go from ubuntu to kubuntu, by adding kubuntu-desktop package, and vice-versa.  All package are there for all versions.

---

### Post by doas777 on 2011-07-08
> **ajgreeny said:**
> 
In effect that means you can turn anything into anything else; as you suggest you can go from ubuntu to kubuntu, by adding kubuntu-desktop package, and vice-versa.  All package are there for all versions.
Indeed. installing the full gnome desktop on a server is a simple:
```
sudo apt-get install ubuntu-desktop
```

---

### Post by wojox on 2011-07-08
Main difference between the two is the [optimized kernel]("https://help.ubuntu.com/10.04/serverguide/C/preparing-to-install.html").

The Server Edition uses the Deadline I/O scheduler instead of the CFQ scheduler used by the Desktop Edition.

Preemption is turned off in the Server Edition.

The timer interrupt is 100 Hz in the Server Edition and 250 Hz in the Desktop Edition.

---

### Post by Skaperen on 2011-07-12
> **ajgreeny said:**
> The repositories available are exactly the same and completely independent of the version of ubuntu (or kubuntu, or xubuntu, etc etc) that you start from.

In effect that means you can turn anything into anything else; as you suggest you can go from ubuntu to kubuntu, by adding kubuntu-desktop package, and vice-versa.  All package are there for all versions.

So, if one is building a "list of all packages", then it would be distinct only for the architecture (just i386 vs amd64 in the latest versions) and the version (e.g. 10.10 vs 11.04, etc).

---

