---
title: "dpkg error can not install/uninstall/upgrade/purge"
date: 2013-06-19
forum: Installation &amp; Upgrades
---

### Post by seruling on 2013-06-19
I receive these error everytime trying to upgrade/install/remove/purge a package:

```
[COLOR=#333333]Processing triggers for initramfs-tools ...
[/COLOR]update-initramfs: Generating /boot/initrd.img-3.8.0-21-generic
cp: cannot stat ‘/module-files.d/libpango1.0-0.modules’: No such file or directory
cp: cannot stat ‘/modules/pango-basic-fc.so’: No such file or directory
E: /usr/share/initramfs-tools/hooks/plymouth failed with return 1.
update-initramfs: failed for /boot/initrd.img-3.8.0-21-generic with 1.
dpkg: error processing initramfs-tools (--configure):
 subprocess installed post-installation script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing: initramfs-tools 
[COLOR=#333333]E: Sub-process /usr/bin/dpkg returned an error code (1)[/COLOR]
```

the error came from libpango1.0-0 and initramfs-tools

Already trying:
[LIST=1]
[*]apt-get -f install
[*]purge old linux-image
[*]purge libpango1
[*]replace libpango1 with libpango1-dev
[*]reinstall initramfs-tools
[*]etc I got from forum
[/LIST]

All failed and always get same error.

System info:
- Ubuntu 13.04 i386
- added GNOME shell
- added xfce4
- current active linux-image: 3.8.0-21-generic

---

### Post by seruling on 2013-06-24
It solved by clicking "Update" (all update) from software updater.
didn't use any terminal command or synaptic.

---

