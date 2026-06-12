---
title: "Unmet dependencies and held broken packages"
date: 2014-05-08
forum: Installation &amp; Upgrades
---

### Post by gillk on 2014-05-08
I'm wondering if someone can help me decipher some errors I am getting from aptitude.

I'm trying to reinstall console-setup. Running sudo apt-get install console-setup gives me the following:

```
Some packages could not be installed. This may mean that you haverequested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies:
 console-setup : Depends: keyboard-configuration but it is not going to be installed
                 Depends: initramfs-tools (>= 0.85eubuntu12) but it is not going to be installed
                 Depends: kbd (>= 1.15-1ubuntu3)
                 Depends: upstart-job
E: Unable to correct problems, you have held broken packages.

```

Fair enough. So then I run  sudo apt-get install console-setup keyboard-configuration initramfs-tools kbd upstart-job. The result:

```
... The following packages have unmet dependencies:
 initramfs-tools : Breaks: console-setup (< 1.72) but 1.70ubuntu7 is to be installed
E: Unable to correct problems, you have held broken packages.
```

Any ideas on what to do? On the face of it there's a version issue, but it seems that I'm within the proper parameters (< 1.72) so why the error?

Thanks!

---

### Post by TheFu on 2014-05-08
Try **aptitude**, not apt-get.
Also - be certain that you've run **sudo aptitude update** first.

---

