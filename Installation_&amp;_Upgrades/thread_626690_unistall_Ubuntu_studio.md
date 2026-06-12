---
title: "unistall Ubuntu studio"
date: 2007-11-29
forum: Installation &amp; Upgrades
---

### Post by nbo10 on 2007-11-29
I have Ubuntu 7.10 and installed Ubuntu studio to check it out and now would like to go back to the plain version. How would I do that. Thanks

---

### Post by logos34 on 2007-11-29
You mean you installed it on a separate partition, or you installed ubuntustudio-desktop? If the former then just reinstall grub, pointing to your ubuntu root partition.  Then use gparted to format or delete the ubuntustudio partition.  If the latter, reinstall the ubuntu-desktop (it will delete ubuntustudio-desktop and restore the ubuntu themes/splash/sounds etc).

---

