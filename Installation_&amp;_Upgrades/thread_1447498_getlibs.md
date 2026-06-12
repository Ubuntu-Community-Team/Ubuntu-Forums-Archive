---
title: "getlibs"
date: 2010-04-05
forum: Installation &amp; Upgrades
---

### Post by albertz on 2010-04-05
Hey,

I wonder if there is an active getlibs thread somewhere. I only found the closed old thread:
[http://ubuntuforums.org/showthread.php?t=474790](http://ubuntuforums.org/showthread.php?t=474790)

I wonder if this is even still maintained or kind of dead (as it doesn't work for me and I think my case I kind of straight forward - more on that later).

I also wonder why getlibs is not in the standard Ubuntu repository.

---

More specific, on my 64bit system, I want to run the 32bit tool pipsplus-monitor. That fails with:

```
gz@gcomputer:~$ pipsplus-monitor 
pipsplus-monitor: error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory

```

So I grabbed getlibs and tried it:

```
gz@gcomputer:~$ sudo ./getlibs /usr/bin/pipsplus-monitor 
libgtk-1.2.so.0: libgtk1.2
No match for libgdk-1.2.so.0
libgmodule-1.2.so.0: libglib1.2
No match for libglib-1.2.so.0
The following i386 packages will be installed:
libglib1.2
libgtk1.2
Continue [Y/n]? 
libglib1.2 was not found in your repositories
Make sure you have all repositories enabled and updated
libgtk1.2 was not found in your repositories
Make sure you have all repositories enabled and updated
No packages to install

```

And I have all repositories enabled (or at least I haven't changed anything after the base install) and updated.

Thanks in advance,
Albert

---

