---
title: "upgrade from 10.04 to 12"
date: 2013-02-26
forum: Installation &amp; Upgrades
---

### Post by bunty2k2002 on 2013-02-26
Setting up language-pack-gnome-en-base (1:12.04+20130128) ...

Setting up tasksel (2.88ubuntu9) ...

Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.32-33-generic
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_IN.cache...
ERROR: Cannot import gmenu, is a package upgrade in progress?
Processing triggers for python-support ...
Errors were encountered while processing:
 memtest86+
 ubuntu-standard
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by bunty2k2002 on 2013-02-26
Setting up memtest86+ (4.20-1.1ubuntu1) ...
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.32-33-generic
Found initrd image: /boot/initrd.img-2.6.32-33-generic
Found memtest86+ image: /boot/memtest86+.bin
/etc/grub.d/README: 2: /etc/grub.d/README: All: not found
/etc/grub.d/README: 4: /etc/grub.d/README: 00_*:: not found
/etc/grub.d/README: 5: /etc/grub.d/README: 10_*:: not found
/etc/grub.d/README: 6: /etc/grub.d/README: Syntax error: "(" unexpected
dpkg: error processing memtest86+ (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of ubuntu-standard:
 ubuntu-standard depends on memtest86+; however:
  Package memtest86+ is not configured yet.
dpkg: error processing ubuntu-standard (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                          Errors were encountered while processing:
 memtest86+
 ubuntu-standard

---

### Post by BLOODBANKER on 2013-03-03
Hi, Bunty2k2002. I have found that it is much better to do a clean full install of a newer version instead of trying to upgrade. These versions are so different from each other, its no wonder you're having problems. Make sure you save the data you want to keep from your old system and do a clean full install.

---

