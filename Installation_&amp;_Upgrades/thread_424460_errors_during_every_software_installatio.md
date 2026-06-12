---
title: "errors during every software installatio"
date: 2007-04-26
forum: Installation &amp; Upgrades
---

### Post by A-1337 on 2007-04-26
Hello!
I get this error "E: linux-image-2.6.20-15-generic: subprocess post-installation script returned error exit status 2" every time I start synaptic and install/remove something. What should I do?

---

### Post by A-1337 on 2007-04-26
It's all because errors during kernel package installation. I've copied some synaptic log messages:
```

Preconfiguring packages ...
Selecting previously deselected package linux-image-2.6.20-15-386.
(Reading database ... 118238 files and directories currently installed.)
Unpacking linux-image-2.6.20-15-386 (from .../linux-image-2.6.20-15-386_2.6.20-15.27_i386.deb) ...
Done.
Setting up linux-image-2.6.20-15-386 (2.6.20-15.27) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.20-15-386
The provided postinst hook script [/sbin/update-grub] could not be run.
dpkg: error processing linux-image-2.6.20-15-386 (--configure):
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 linux-image-2.6.20-15-386
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up linux-image-2.6.20-15-386 (2.6.20-15.27) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.20-15-386

```

It seems he can't finish this installation and tries it over and over again. Please, help!

---

