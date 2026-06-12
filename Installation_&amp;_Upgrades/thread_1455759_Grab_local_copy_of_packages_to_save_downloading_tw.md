---
title: "Grab local copy of packages to save downloading twice?"
date: 2010-04-16
forum: Installation &amp; Upgrades
---

### Post by davidpbrown on 2010-04-16
Just for fun, I'm wondering if I can grab a copy of the Lucid packages that my laptop's downloading and dump them into a directory on the desktop computer, then upgrade the desktop in a way it makes use of the packages it wants and that I have to hand already.

Is that possible?

---

### Post by dominiquec on 2010-04-16
You can, with AptOnCD.

```
sudo apt-get install aptoncd
```

---

### Post by mk1w86 on 2010-04-16
I would also recommend AptonCD. :grin:

Another way you can do it is in Synaptic, mark the packages that you want to install/upgrade then go to File >> Generate package download script.  There is a guide here:

[https://help.ubuntu.com/community/Synaptic/PackageDownloadScript](https://help.ubuntu.com/community/Synaptic/PackageDownloadScript)

There are also various other ways you can do it using apt on the command line, see here for more details:

[https://help.ubuntu.com/community/AptGet/Offline](https://help.ubuntu.com/community/AptGet/Offline)

---

