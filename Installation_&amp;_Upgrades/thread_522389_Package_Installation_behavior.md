---
title: "Package Installation behavior"
date: 2007-08-10
forum: Installation &amp; Upgrades
---

### Post by core_dump on 2007-08-10
I'm building debian packages that run on Ubuntu and I need to test them. One great thing for that is debootstrap and then I install my packages into the freshly created virgin Ubuntu system.

But one thing that bother me is that by default, when apt-get install a package that provide a service running constantly, such as apache2, the process is started RIGHT AFTER the package is installed.

Is there a way to prevent a service to start (or restart) when a package is installed (or upgraded). Like debootstrap is doing.

The main goal is to be able to debootstrap Ubuntu, then chroot into it and install package and be sure it won't mess the host.

And I'm looking for a solution that apply to dapper and newer release.

thanks!

---

