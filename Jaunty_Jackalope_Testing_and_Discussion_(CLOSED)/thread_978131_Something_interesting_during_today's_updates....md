---
title: "Something interesting during today's updates..."
date: 2008-11-10
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by gspat on 2008-11-10
This came up...

> Setting up nvidia-cg-toolkit (2.0.0015.deb2) ...
Using '/var/cache/nvidia-cg-toolkit/Cg-2.0_May2008_x86.tgz'
Using '/var/cache/nvidia-cg-toolkit/Cg-2.0_May2008_LanguageSpecification.pdf'
Checking MD5 sum for NVIDIA Cg Toolkit file...passed.
Checking MD5 sum for NVIDIA Cg Toolkit spec file...passed.
Uninstalling NVIDIA Cg Toolkit components: Cg compiler, header files, libraries, documentation, examples, manual pages, (running ldconfig), done.
Uncompressing NVIDIA Cg Toolkit.
Installing NVIDIA Cg Toolkit components: Cg compiler, header files, libraries, documentation, examples, closedir() attempted on invalid dirhandle DIR at /usr/bin/nvidia-cg-toolkit-installer line 305.
closedir() attempted on invalid dirhandle DIR at /usr/bin/nvidia-cg-toolkit-installer line 305.
closedir() attempted on invalid dirhandle DIR at /usr/bin/nvidia-cg-toolkit-installer line 305.
closedir() attempted on invalid dirhandle DIR at /usr/bin/nvidia-cg-toolkit-installer line 305.
closedir() attempted on invalid dirhandle DIR at /usr/bin/nvidia-cg-toolkit-installer line 305.
closedir() attempted on invalid dirhandle DIR at /usr/bin/nvidia-cg-toolkit-installer line 305.
closedir() attempted on invalid dirhandle DIR at /usr/bin/nvidia-cg-toolkit-installer line 305.
manual pages, (running ldconfig), done.


Will post this on launchpad as well... as bug #296565

[https://bugs.launchpad.net/ubuntu/+source/nvidia-cg-toolkit/+bug/296565](https://bugs.launchpad.net/ubuntu/+source/nvidia-cg-toolkit/+bug/296565)

---

### Post by Kevbert on 2008-11-11
Is this a package that you've installed as an extra ? I don't seem to have the file or package on my PC (I'm using the Nvidia 177 driver).

---

### Post by gspat on 2008-11-12
No idea really, I have many extras installed on this one, including KDE stuff and stuff for compiling.

---

