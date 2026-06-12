---
title: "Problem with server kernel source"
date: 2008-10-19
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by lckarssen on 2008-10-19
I've installed Intrepid Server and now I'm trying to get kqemu working. 
When I ran aptitude install kqemu-common I got the following error:
```
Error! Your kernel source for kernel 2.6.27-7-server cannot be found at
/lib/modules/2.6.27-7-server/build or /lib/modules/2.6.27-7-server/source.
Installing initial module

```
So I made sure I had the kernel-source package installed. I checked in /usr/src and the kernel source is there, still packed in bz2 format. Shouldn't this file have been extracted?

---

### Post by lckarssen on 2008-10-19
Sorry about that, apparently I had missed a (necessary) reboot, the problems were a result of the wrong kernel-headers being installed by kqemu-source. 
After a reboot and a reinstall of kqemu-common the build works.

---

### Post by lckarssen on 2008-10-19
Sorry, double post.
This is not my lucky day :-)

---

