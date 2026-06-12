---
title: "no package managers working"
date: 2011-05-05
forum: Installation &amp; Upgrades
---

### Post by Riskexas on 2011-05-05
surfing on the Ubuntu software center i found ¨Platium Arts sandbox gamemaker¨. But it was corrupted! I saw that its corrupted on Ubuntu 11.4, but it was too late. So it corrupt:
anything that i try to install trough package manager (any) fails. Trying to install by terminal (apt-get or something) shows:
```
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem.
```So i write:
```
sudo dpkg --configure -a
```BUT it tries to continue installing ¨Platium Arts sandbox gamemaker¨ (which is corrupt)

What should i do?:confused:

---

### Post by lechien73 on 2011-05-05
Hi,

You could try the following:

Open a terminal window and type:

```
cd /var/lib/dpkg
sudo cp available available.old
sudo cp status status.old
```

Then type:

```
gksu gedit ./available
```

to open the "available" file. Remove all references to the corrupted package, then save and quit. Then type:

```
gksu gedit ./status
```

to open the "status" file. Do the same as before - remove all references to the corrupted package, then save and quit. Then:

```
cd info
```

Delete all files relating to package.

After this, try:

```
sudo dpkg --configure -a
```

again!

This should get you back up and running :)

---

### Post by Riskexas on 2011-05-05
_***YEY IT WORKS AGIAN!!! THANK YOU VERY MUCH!!!!***_ I can live again!!!! URE THA BEST!!!!!!!!!!!!!!!!!!!!
:) :) :) :) :)



BTW it some times mention about it (the package), but it doesn't do anything like: O look strange package... ehh dont care..... :guitar:

---

