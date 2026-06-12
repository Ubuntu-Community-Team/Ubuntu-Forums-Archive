---
title: "g77 installation?"
date: 2007-02-16
forum: Installation &amp; Upgrades
---

### Post by temuchin on 2007-02-16
Hello there,
i have installed ubuntu 6.10 from the desktop cd and just discovered that i don't have g77 (which is needed for some other installations).
i found some tared/zipped g77 stuff on this website, but it is not clear what is the best and smoothest way to install and what components are needed.
can this installation be automated?
(i used apt get .. essential for the g++, but it didn't help with g77)
thanks,
t

---

### Post by LotsOfPhil on 2007-02-16
sudo aptitude install g77

That doesn't work?
When I type:
```
$ sudo aptitude search g77
p   g77                             - The GNU Fortran 77 compiler
p   g77-2.95                        - The GNU Fortran 77 compiler
p   g77-2.95-doc                    - Documentation for the GNU Fortran compiler
p   g77-3.4                         - The GNU Fortran 77 compiler
p   g77-3.4-doc                     - Documentation for the GNU Fortran compiler
p   g77-doc                         - Documentation for the GNU Fortran compiler

```

---

