---
title: "Synaptic Error"
date: 2010-01-18
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by sports fan Matt on 2010-01-18
E:Problem executing scripts dpkg::post-invoke "if {-x/usr/sbin/localepurge}&&( $(ps w -p$PPID grep -c remove !=1}; then usr/sbin/localepurge; else exit 0 fi

E: sub process returned an error code.

Can someone help me understand that error in english and how I can fix it?

---

### Post by SevenMachines on 2010-01-18
what was the package you were try to install/remove? its easier to see with the full command/output

---

### Post by sports fan Matt on 2010-01-18
Started with installing or removing any program.  Gyachi was one..Google Chrome would be another.

---

### Post by SevenMachines on 2010-01-18
seems its a bug in localepurge, should have been fixed in 0.6.2, are you on this version yet?
[https://bugs.launchpad.net/debian/+source/localepurge/+bug/507015](https://bugs.launchpad.net/debian/+source/localepurge/+bug/507015)

localepurge (0.6.2) unstable; urgency=low
.....
  * usr/sbin/localepurge: apply patch sent in by Bert Schulze to fix
    incompatibility with bash 4.1 which broke localepurge. Thanks a
    lot for your contribution, Bert! (closes: #563426, #563427, #563597)
.....

---

### Post by SevenMachines on 2010-01-18
i see 0.6.2 was only published 8 hours ago so it might not have arrived in the repository (or mirror) yet

---

### Post by sports fan Matt on 2010-01-18
Ok...nope still 0.6.1 here

---

