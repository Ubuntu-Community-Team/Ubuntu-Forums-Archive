---
title: "upgrade to lucid and having some kernel problems"
date: 2010-04-06
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by samrobb1 on 2010-04-06
I recently upgraded from 9.10 to 10.04 and since have had some problems with the linux-generic-2.6.32-19-generic kernel. Whenever I install anything through terminal it gives me this error at the end:

```
dpkg: error processing linux-image-2.6.32-19-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.32-19-generic; however:
  Package linux-image-2.6.32-19-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 2.6.32.19.20); however:
  Package linux-image-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          No apport report written because the error message indicates its a followup error from a previous failure.
                                                    Errors were encountered while processing:
 linux-image-2.6.32-19-generic
 linux-image-generic
 linux-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

not sure if this is a big problem but it is a little bit annoying. I tried reinstalling the package again, but it seemed to screw it up even more. Now I can't really install anything; it just says:

```
Error! Your kernel headers for kernel 2.6.31-19-generic cannot be found at /lib/modules/2.6.31-generic/build or /lib/modules/2.6.31-19-generic/source.
```

not really sure what to do or what any of this means

---

### Post by Mark Phelps on 2010-04-06
10.04 is still in beta testing, so please post your beta-related questions to the proper beta testing forum: Development & Programming, Lucid Lynx Testing.  thanks

---

### Post by philinux on 2010-04-06
Thread Moved

---

### Post by samrobb1 on 2010-04-09
i fixed it. i didn't know that i was able to reinstall ubuntu with out formatting the hard drive. just reinstalled, kept all my files and everythings working 100% so far! :D

---

