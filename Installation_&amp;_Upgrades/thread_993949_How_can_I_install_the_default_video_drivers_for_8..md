---
title: "How can I install the default video drivers for 8.10"
date: 2008-11-26
forum: Installation &amp; Upgrades
---

### Post by Bill Roberts on 2008-11-26
I installed the Restricted Driver nvidia-glx-177.  Now I can only boot to a command line.

I have researched this forum and the ubuntu documentation and tried all of the fixes, but none have succeeded.

Removing the Restricted Drivers doesn't resolve the problem.

Does anyone know how I can re-install the drivers that were originally installed when I installed 8.10 from the iso.  What packages?

I don't want to do a full re-install.

---

### Post by renzokuken on 2008-11-26
try

```
sudo dpkg-reconfigure xserver-xorg
```

from the command line and run through the wizard selecting either the **nv** or **vesa** driver in the appropriate section.

then try again

---

### Post by icanfly0307 on 2008-11-26
If renzokuken's suggestion doesn't work, try booting into "Recovery Mode" in the GRUB menu and select "xfix" from the list of options.

---

