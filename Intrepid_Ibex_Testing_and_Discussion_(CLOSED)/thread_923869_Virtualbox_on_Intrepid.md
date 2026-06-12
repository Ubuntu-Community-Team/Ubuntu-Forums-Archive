---
title: "Virtualbox on Intrepid"
date: 2008-09-18
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by pdwerryhouse on 2008-09-18
Hi all,

Just some notes on the issues I faced trying to get virtualbox-ose running on intrepid (my PC is very new, and neither the SATA controller nor ethernet are supported on Hardy).

Unfortunately, the kernel is linux-image-2.6.27-3-server, and the only virtualbox-ose modules available are for a 2.6.27-5 kernel (which doesn't exist in the archive).

I've also installed the virtualbox-ose-source package to try to build the modules myself, but there appears to be a problem with the package:

```

# module-assistant a-i virtualbox-ose
[...]
The source tarball could not be found!
Package virtualbox-ose not installed?

```

There isn't a /usr/src/virtualbox-*.tar.bz2 file at all, as the README.Debian file says there should be - instead, the source appears to already be unpacked into /usr/src/vboxdrv-2.0.2

Once I changed into this directory, ran make ; make install and then manually loaded the vboxdrv module, all was well after that.

Cheers,

Paul

---

### Post by Quikee on 2008-09-19
The kernel modules for virtualbox are now automatically compiled and installed via dkms and not anymore through provided modules (the same goes for nvidia drivers for example). 

You should check if you have vboxdrv in "/var/lib/dkms" and if "sudo invoke-rc.d dkms_autoinstaller start" lists vboxdrv.

---

### Post by pdwerryhouse on 2008-09-19
Ah, ok, thanks. That's certainly new to me.

Well, it definitely wasn't installing it automatically. Now that I've figured out how it all works, it is, but it wasn't beforehand and there was certainly nothing in the virtualbox packaged docs that indicated that this is how it should be handled.

Cheers.

---

