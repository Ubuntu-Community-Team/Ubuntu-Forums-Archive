---
title: "policykit-gnome, gnome-mount and libpolkit-gnome0 no longer needed?"
date: 2009-10-18
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by jrothwell97 on 2009-10-18
Running sudo apt-get autoremove earlier today produces this:

```
jonathan@Bronowski:~$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED
  gnome-mount libpolkit-gnome0 policykit-gnome
0 upgraded, 0 newly installed, 3 to remove and 10 not upgraded.
After this operation, 1,712kB disk space will be freed.
Do you want to continue [Y/n]? n

```

I'm pretty certain that gnome-mount and the PolicyKit bindings are still required... is this a packaging bug, or is it intended?

---

### Post by chrisccoulson on 2009-10-18
Nope, they're all deprecated now, and nothing on the default install requires the old Policykit

---

### Post by jrothwell97 on 2009-10-18
Aha, they're being deprecated. That makes sense. Thanks!

---

### Post by cariboo on 2009-10-18
I don't have any of those files installed either, every thing seems to work OK without them. From the looks of it the policykit files are replace with policykit-1-gnome. My eSATA drive mounts automagically when plugged in and turned on. I still have to enter my password though.

---

