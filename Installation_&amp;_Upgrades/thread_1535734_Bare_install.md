---
title: "Bare install"
date: 2010-07-21
forum: Installation &amp; Upgrades
---

### Post by kempy1000 on 2010-07-21
Hi,

Is it possible to install a super bare ubuntu install? I mean just a bash shell and some basic programs eg apt?

Even bare-er than the minimal install cd.

I read something about a bootstrap install to get a bare system?

Thanks
Chris

---

### Post by dv3500ea on 2010-07-21
[https://help.ubuntu.com/community/Installation/MinimalCD]("https://help.ubuntu.com/community/Installation/MinimalCD")
I think what you want is only the contents of the ubuntu-minimal metapackage.

---

### Post by kempy1000 on 2010-07-21
Thank you I had no idea that existed

---

### Post by sisco311 on 2010-07-21
The minimal CD, just like the alternate CD in cli only mode, installs a boot loader (Grub by default), a kernel, ubuntu-minimal and ubuntu-standard. The only difference is that the minimal CD downloads the packages from the repositories over the internet or a local network.

Yes, you can use debootstrap to install a bare bone system, by default debootstrap installs less packages than ubuntu-minimal.

Take a look at: 
[uhelp]community/DebootstrapChroot[/uhelp]
after you create a chroot environment you can install a kernel & a boot loader and boot into your new system. :)

This guides are a little outdeted by still provide usefull information:
[uhelp]community/Installation/FromKnoppix[/uhelp]
[uhelp]8.04/installation-guide/i386/linux-upgrade.html[/uhelp]

---

