---
title: "Installing as super user"
date: 2008-11-16
forum: Installation &amp; Upgrades
---

### Post by PhiberOptik24 on 2008-11-16
Hey guys, I tried installing the latest ATI driver for my graphics card 3870xt and downloaded the file on my desktop, double-click and ran it in terminal.  Here's the message that i get.

[IMG]http://i25.photobucket.com/albums/c77/VoodooChild24/Screenshot.png[/IMG]

Can anyone help me on what to do next?  I'm new to Linux.
Any help would be very much appreciated.

---

### Post by cariboo on 2008-11-16
Open a Applications-->Accessories-->Terminal and type:

```
cd Desktop
```

Next in the same terminal type:

```
sudo ./*run
```

This will install the driver as root.

Jim

---

### Post by PhiberOptik24 on 2008-11-16
Hey Jim,

When I enter cd desktop in the terminal, this is what it gives me.

[IMG]http://i25.photobucket.com/albums/c77/VoodooChild24/Screenshot2.png[/IMG]

"No such file in directory" is the message that I get.

---

### Post by bettlebrox on 2008-11-16
It's case sensitive; desktop isn't the same as Desktop.

If your new to Linux your probably better off installing the version of the module (driver) that Ubuntu packages.

See [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI) for more details, but basically:

[INDENT]Open the restricted drivers manager in "System -> Administration -> Restricted Drivers Manager" and select "ATI accelerated graphics driver". [/INDENT]

---

