---
title: "test kernel for Intrepid but on Hardy"
date: 2008-11-21
forum: Installation &amp; Upgrades
---

### Post by linuxonbute on 2008-11-21
I am running Hardy which does not handle my elantech touchpad properly.

There have been some developments and I have tested with the live Intrepid distro but it still does not work. 

Since then I have been asked to test an Intrepid kernel with the bug fix backported to it. I have downloaded it and wanted to install it in Hardy.

Running Gdebi gives me this message :

Package Linux-Image-2.6.27-10-generic

Status : all dependencies are satisfied

"Linux kernel image for version 2.6.27 on x86/x86_64
This package contains the Linux kernel image for version 2.6.27 on x86/x86_64.
Also includes the corresponding System.map file, the modules built by the packager, and scripts that try to ensure that the system is not left in an unbootable state after an update.
Supports Generic processors.
Geared toward desktop systems.
You likely do not want to install this package directly. Instead, install the linux-generic meta-package, which will ensure that upgrades work correctly, and that supporting packages are also installed."

Can anyone tell me what would happen if I continue to install it? 
Thanks

---

### Post by linuxonbute on 2008-11-21
Or perhaps someone can tell me what i actually do to get this to work :-

"You likely do not want to install this package directly. Instead, install the linux-generic meta-package, which will ensure that upgrades work correctly, and that supporting packages are also installed."

What is this linux-generic meta-package?
thanks

---

### Post by kgr132 on 2008-11-21
A meta-package is referenced in the Ubuntu package manager and is a list of a bunch of supporting application packages that work together in a particular distribution. It saves the user from needing to find and install the individual packages. They can use the meta-package to get the whole group of packages at one time. I believe that the update package you were sent wants you to use a new kernel meta-package in order to update some of the kernel related packages and assure compatibility with the Intrepid kernel. It's possible that installing the Intrepid kernel into a Hardy installation without the supporting meta-package for the new kernel could cause some problems with regard to the kernel related packages and the new package installer is warning you of that possibility.

If I were you, I either go back to the people who asked you to test this new Intrepid kernel and question them regarding the message you received, or else use another hdd to test this new kernel in a separate, clean install of Intrepid. Also remember, you can't back up your data, particularly your /home partition, too often when you're fooling around with custom kernels.

Good Luck, 
-K-

---

