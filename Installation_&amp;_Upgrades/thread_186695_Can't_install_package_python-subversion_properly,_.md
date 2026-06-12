---
title: "Can't install package python-subversion properly, dpkg problem?"
date: 2006-06-02
forum: Installation &amp; Upgrades
---

### Post by brasse on 2006-06-02
I am trying to install the python-subversion package, but something is wrong. When I do 'apt-get install' I get the following error message:
```

dpkg: ../../src/packages.c:191: process_queue: Assertion `dependtry <= 4' failed

```
'dpkg -l | grep -v ^ii' says that the status of python-subversion is 'iU'. I guess that something went wrong when installing the package? How would I go about troubleshooting this? Perhaps someone has a quick fix?

All help will be greatly appriciated!

Regards,
Mattias

---

### Post by jobezone on 2006-06-02
This is definetly a bug, I've just tried installing this as well, and get the same error. Searched around, and I found that it's about a circular dependency (a depends of b which depends of a). To fix, I would think that installing the python-subversive package with **sudo dpkg -i --force-depends package.deb** could fix it. The package is in **/var/cache/apt/archives**.
I wonder if this bug (;-) has already been reported on launchpad.net . . .

---

### Post by brasse on 2006-06-02
I have reported the bug, hopefully at the correct place: [https://launchpad.net/bugs/46977](https://launchpad.net/bugs/46977)
I have not heard anything back yet though.

:.:: mattias

---

