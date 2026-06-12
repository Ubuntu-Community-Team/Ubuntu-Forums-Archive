---
title: "Synaptic Package Manager"
date: 2008-08-14
forum: Installation &amp; Upgrades
---

### Post by ash_mall on 2008-08-14
Hi,

I am totally new to Ubuntu and i am getting an error message on Synaptic package Manager. I was installing Virtual box in Ubuntu so i can use windows also.


E: The package Virtualbox needs to be reinstalled but i cant find an archive for it.
E:Internet error opening cache (1) Please report.

---

### Post by theyranos on 2008-08-14
Open up a terminal and type
```
sudo dpkg -r virtualbox
``` and let us know what happens (it's supposed to uninstall virtualbox, but since Synaptic is confused, your best bet is probably to uninstall and reinstall).

If it succeeds (and if Synaptic is no longer messed up), you should be able to install virtualbox (look for the **virtualbox-ose** and **virtualbox-ose-modules** packages) without a problem.

---

### Post by ash_mall on 2008-08-14
I have tried that command but i got another message:

dpkg: status database area is locked by another process

then i typed: sudo killall synaptic
after that i typed: sudo dpkg -r virtualbox
and i got another error message
dpkg: error processing virtualbox (--remove):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
Errors were encountered while processing:
 virtualbox

---

### Post by theyranos on 2008-08-14
```

sudo dpkg --force-all -r virtualbox

```

will override that. Once it's gone, use Synaptic to find and uninstall anything that starts with virtualbox-ose. I'm guessing you have one of the virtualbox-ose-modules* packages installed (since that's what caused exactly the same errors on my machine three days ago :)). Remove those too (synaptic should be able to get them, if not, you can force the issue with dpkg), and you should be okay to try the install again.

If you want the open-source one, you'll want to reinstall virtualbox-ose and the virtualbox-ose-modules package that corresponds to your kernel (the last part of **uname -r** will be the kernel type. Probably "generic.")

if you want the one from Sun's downloads page, download the .deb somewhere and use **sudo dpkg -i *filename.deb*** to install it.

**Edit:** *Sun's virtualbox package and virtualbox-ose-modules don't get along on the same system. Sun should've listed virtualbox-ose-modules as a conflicting package, but they didn't. Hence, if you try to install Sun's virtualbox on a machine that previously had virtualbox-ose, Synaptic will remove the virtualbox-ose package as a conflict, but it won't know to also remove the virtualbox-ose-modules package.*

---

