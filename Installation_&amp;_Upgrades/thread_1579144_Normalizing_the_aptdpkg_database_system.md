---
title: "Normalizing the apt/dpkg database system"
date: 2010-09-21
forum: Installation &amp; Upgrades
---

### Post by fmouse on 2010-09-21
I recently upgraded to lucid from a previous Ubuntu version on a laptop.  The hard drive on the laptop is old, with only 20G or so of drive space, and I ran out of drive space at one point, which threw the upgrade off track.  To make more space, I manually (at the CLI) deleted a lot of stuff, such as old /lib/module hierarchies, downloaded and previously installed packages, kernel header and source trees and such.  I've since gotten things working pretty well, however I have some inconsistencies in the package database which I'd like to get rid of.  Everything I try on these returns an error and nothing gets changed.  For example, I have the linux-ubuntu-modules-2.6.24-26-386 package installed, and aptitude shows the state as "H" (half installed) and the action as "d" (marked for deletion), but I can neither fully delete it nor fully install it.  The .deb is gone, although the postrm script is still there.

What do I need to do to clean up the dpkg database and get rid of references to these packages?

---

### Post by fmouse on 2010-09-21
There seems to be no easy way to take care of this problem.  In this case, I ran:

```
dpkg --force-remove-reinstreq --remove linux-ubuntu-modules-2.6.24-26-386
```

In the output, I got the following two lines:

```
WARNING: Couldn't open directory /lib/modules/2.6.24-28-386: No such file or directory
FATAL: Could not open /lib/modules/2.6.24-28-386/modules.dep.temp for writing: No such file or directory
```

So I ran:

```
# mkdir/lib/modules/2.6.24-26-386
# touch /lib/modules/2.6.24-28-386/modules.dep.temp
```

And then re-ran: 

```
dpkg --force-remove-reinstreq --remove linux-ubuntu-modules-2.6.24-26-386
```

dpkg found its missing file and directory and completed the task.

There ought to be an easier way to do this!

---

