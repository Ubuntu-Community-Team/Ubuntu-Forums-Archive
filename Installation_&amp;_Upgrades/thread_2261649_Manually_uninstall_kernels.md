---
title: "Manually uninstall kernels"
date: 2015-01-20
forum: Installation &amp; Upgrades
---

### Post by Alistair_Grant on 2015-01-20
Hi,


I'm working on resolving some USB3 issues on my Dell XPS13 laptop and as part of the search have compiled and manually installed a number of kernels.  Looking for files / directories with the kernel name I get:


[FONT=courier new]/lib/modules/3.18.0-rc4mathias0.1+[/FONT]
[FONT=courier new]/var/lib/initramfs-tools/3.18.0-rc4mathias0.1+[/FONT]
[FONT=courier new]/boot/System.map-3.18.0-rc4mathias0.1+[/FONT]
[FONT=courier new]/boot/vmlinuz-3.18.0-rc4mathias0.1+[/FONT]
[FONT=courier new]/boot/config-3.18.0-rc4mathias0.1+[/FONT]
[FONT=courier new]/boot/initrd.img-3.18.0-rc4mathias0.1+[/FONT]
[FONT=courier new]/var/lib/dkms/vboxhost/4.3.20/3.18.0-rc4mathias0.1+[/FONT]
[FONT=courier new]/var/lib/dkms/vboxhost/kernel-3.18.0-rc4mathias0.1+-x86_64[/FONT]


I'm pretty confident that I can just delete the first 6 files / directories and re-run update-grub, however I'm not so sure about the last two (/var/lib/dkms/vboxhost/...).


Can anyone confirm that it is OK to simply delete these files, or is there another process I should be following to manually uninstall kernels?


Thanks very much,
Alistair

---

### Post by TheFu on 2015-01-20
If the files were created using a package manager, then it is smart to remove them using the package manager.  If you manually remove files that are part of a package, the package manager may refuse to allow "remove" of the package.

---

### Post by Alistair_Grant on 2015-01-20
> **TheFu said:**
> If the files were created using a package manager, then it is smart to remove them using the package manager.  If you manually remove files that are part of a package, the package manager may refuse to allow "remove" of the package.

Thanks for your reply, perhaps I should have been a bit more explicit.  What I meant by compiled and manually installed is that I used:

```
$ make
$ sudo make modules_install install
```
The kernels that were installed via a package manager I will remove using the package manager.

---

### Post by ubfan1 on 2015-01-20
Check the makefile for an "uninstall" target, that would be the cleanest way to ensure you get the right things.

---

### Post by Alistair_Grant on 2015-01-21
> **ubfan1 said:**
> Check the makefile for an "uninstall" target, that would be the cleanest way to ensure you get the right things.

It would, but unfortunately there isn't an uninstall target, or anything similar.

Thanks for your reply,
Alistair

---

