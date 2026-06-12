---
title: "Is there a .deb package for make that I can download?"
date: 2019-04-13
forum: Installation &amp; Upgrades
---

### Post by frejock on 2019-04-13
Hi all,
Ubuntu user here since 2007. I recently bought a Lenovo Ideapad and struggling to get wireless to work. I do not have an ethernet line. I downloaded the source for the Realtek wireless driver but I am unable to build it since make is not present in the Bionic Xfce AMD64 version I just installed :(

i download .deb versions of make and make-guile but when I run make it is missing some libguile-2.0 libraries. Before I go further down this rabbit hole, I would like to know if there is a .deb version of essential make and other build tools which I can safely go with?

Anyone has a solution? (Needless to say, I am very upset with Lenovo for going with Realtek and not providing a wireless driver for the linux family)

---

### Post by Holger_Gehrke on 2019-04-13
The package you're looking for is probably 'build-essential', a meta-package that depends on the C and C++ compilers, make and the development files for libc. You're probably going to need some more '*-dev' packages for the various libraries the driver needs; there should be a text file included with the source-code telling you which libraries these are.

Holger

---

### Post by Impavidus on 2019-04-13
The essential packages should be present on the live disk you used for install. Plug the live disk in (on your installed system, not as a live session), enable the repository on the live disk and try to install build-essential.

---

### Post by kc1di on 2019-04-13
You also should install dkms which is found on the live usb. (under /pool/ main /d )It will be needed to install the driver to the kernel.

---

