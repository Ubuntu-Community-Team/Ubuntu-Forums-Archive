---
title: "Clearing an apt-get installation that broke while installing"
date: 2007-01-14
forum: Installation &amp; Upgrades
---

### Post by kombucha on 2007-01-14
I tried installing k3d earlier today through apt-get, and something went wrong while it was installing. I don't really care, because I just wanted to try it out, but now every time I install or uninstall a program using apt-get or synaptic or dpkg or anything, I get a notice about k3d having an error: "E: k3d: subprocess post-installation script returned error exit status 1 I"
I've tried removing it and purging it, but those don't work. How can I flush it from my system, or at least avoid this error?
Thanks! ](*,)

---

### Post by kingmonkey on 2007-01-14
Try typing

```
 sudo dpkg-reconfigure cdrecord 
```

---

### Post by kerry_s on 2007-01-14
Try running in terminal-> sudo apt-get -f install

---

### Post by kombucha on 2007-01-14
Alright, the first suggestion brings up a configure screen for burning CD privileges... the second suggestion I believe just attempts to reinstall it? Here is what I get:

> Setting up k3d (0.5.12.0-1ubuntu2) ...
Traceback (most recent call last):
  File "/usr/bin/pycentral", line 1348, in ?
    main()
  File "/usr/bin/pycentral", line 1342, in main
    rv = action.run(global_options)
  File "/usr/bin/pycentral", line 865, in run
    pkg.read_version_info()
  File "/usr/bin/pycentral", line 535, in read_version_info
    raise PyCentralError, "package has no field Python-Version"
__main__.PyCentralError: package has no field Python-Version
dpkg: error processing k3d (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 k3d
E: Sub-process /usr/bin/dpkg returned an error code (1)


Seemingly some sort of python error? Let me go check if Python is installed...

Yes, it seems that way.

Any other ideas?

---

### Post by Arathorn on 2007-01-21
I've got the same issue. I just wanted to check out K3D, now I just want to get rid of it. Any help is appreceated.

---

### Post by wpshooter on 2007-01-21
First I believe I would have installed it thru add/remove programs.

Have you gone into synaptic and did a NAME search on k3b and then attempted to do a COMPLETE uninstall of it ?

---

### Post by Arathorn on 2007-01-21
I've installed K3D with Adept. When I select uninstall or purge the K3D package and apply, I get an error when trying to uninstall or purge it. What exactly do you mean with a complete uninstall?

---

### Post by Arathorn on 2007-01-23
Anyone?

---

### Post by LN&quot; on 2007-01-25
This bug report should help you out.

[https://launchpad.net/ubuntu/+source/k3d/+bug/64848](https://launchpad.net/ubuntu/+source/k3d/+bug/64848)

---

