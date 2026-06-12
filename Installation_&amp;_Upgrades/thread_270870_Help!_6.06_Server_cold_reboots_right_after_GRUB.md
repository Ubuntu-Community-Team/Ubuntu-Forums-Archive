---
title: "Help! 6.06 Server cold reboots right after GRUB"
date: 2006-10-03
forum: Installation &amp; Upgrades
---

### Post by rapha on 2006-10-03
Hi all!

I'm trying to set up Ubuntu 6.06 Server on an old PI MMX. Installation went just fine, I got network and everything. However, after removing the CD and rebooting, I get GRUB and then a restart. Over and over again.

Using the rescue mode I dist-upgraded the system to the newest kernel; still the same problem. The machine has 48M of RAM, which checks out just fine using Memcheck.

init=/bin/sh for a bootflag doesn't change the behaviour.

Is there anything I can do about this? I'd be grateful for even the smallest hints in diagnosing what is going on.

Best regards,
Raphael

---

### Post by az on 2006-10-03
The server kernel only runs on a Pentium II or better (i686).  You may run a server using the desktop kernel which will run fine on a pentium I (i386)

You can use the alternate cd to install a server with that kernel.  Either reinstall or boot the installer, chroot into your install and install the linux-image-2.6.xxxx package from the /pool directory on the cd.


The installer on all the cds uses the desktop kernel.  That's why the install went fine and now won't work.

---

### Post by rapha on 2006-10-04
Hi azz,

chrooting and installing the -386 kernel worked like a charm, thanks! 

Why don't they build the initial server kernel for 386 as well and offer more optimised kernels as an option, like for the desktop installations. Is that known?

-- Raphael

---

### Post by az on 2006-10-04
> **rapha said:**
> Hi azz,

chrooting and installing the -386 kernel worked like a charm, thanks! 

Why don't they build the initial server kernel for 386 as well and offer more optimised kernels as an option, like for the desktop installations. Is that known?

-- Raphael

It is what it is.  I think there is a spec for future versions to autodetect and install the apropriate kernel in the server version.  But I am not sure.

---

### Post by rapha on 2006-10-05
Hum. Well, c'est la vie I guess :)

---

