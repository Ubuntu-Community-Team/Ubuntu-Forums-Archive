---
title: "During upgrade from 18.04.5 to 20.04.1, a grub-efi-amd64-signed package error recv'd"
date: 2020-10-05
forum: Installation &amp; Upgrades
---

### Post by tomdkat on 2020-10-05
During the upgrade from 18.04.5 to 20.04.1, this error was received:

```
installed grub-efi-amd64-signed package post-installation script subprocess returned error exit status 255
```

I proceeded with the upgrade, even though I was told the upgrade failed.  So far, the system continues to boot fine.   Is this something I should be concerned with, given the system continues to boot ok?

Thanks in advance!

Peace...

---

### Post by tomdkat on 2020-10-08
So, I have more information.  I noticed Ubuntu 20.04 wasn't updating itself, so I manually performed an update and found the following:

```

Unpacking gir1.2-mutter-6:amd64 (3.36.6-1ubuntu0.20.04.2) over (3.36.4-0ubuntu0.20.04.2) ...
Preparing to unpack .../libmutter-6-0_3.36.6-1ubuntu0.20.04.2_amd64.deb ...
Unpacking libmutter-6-0:amd64 (3.36.6-1ubuntu0.20.04.2) over (3.36.4-0ubuntu0.20.04.2) ...
Preparing to unpack .../mutter_3.36.6-1ubuntu0.20.04.2_amd64.deb ...
Unpacking mutter (3.36.6-1ubuntu0.20.04.2) over (3.36.4-0ubuntu0.20.04.2) ...
Setting up grub-efi-amd64-signed (1.142.6+2.04-1ubuntu26.4) ...
od: /sys/firmware/efi/efivars/SecureBoot-8be4df61-93ca-11d2-aa0d-00e098032b8c: read error: Interrupted system call
/usr/share/grub/grub-check-signatures: 22: [: Illegal number: 
dpkg: error processing package grub-efi-amd64-signed (--configure):
 installed grub-efi-amd64-signed package post-installation script subprocess returned error exit status 255
dpkg: dependency problems prevent configuration of shim-signed:
 shim-signed depends on grub-efi-amd64-signed | grub-efi-arm64-signed; however:
  Package grub-efi-amd64-signed is not configured yet.
  Package grub-efi-arm64-signed is not installed.

dpkg: error processing package shim-signed (--configure):
 dependency problems - leaving unconfigured
Setting up mutter-common (3.36.6-1ubuntu0.20.04.2) ...
No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                          Processing tri
ggers for desktop-file-utils (0.24-1ubuntu3) ...
Processing triggers for mime-support (3.64ubuntu1) ...
Processing triggers for gnome-menus (3.36.0-1ubuntu1) ...
Processing triggers for libglib2.0-0:amd64 (2.64.3-1~ubuntu20.04.1) ...
Processing triggers for libc-bin (2.31-0ubuntu9.1) ...
Processing triggers for man-db (2.9.1-1) ...
Setting up libmutter-6-0:amd64 (3.36.6-1ubuntu0.20.04.2) ...
Setting up gir1.2-mutter-6:amd64 (3.36.6-1ubuntu0.20.04.2) ...
Setting up mutter (3.36.6-1ubuntu0.20.04.2) ...
Processing triggers for libc-bin (2.31-0ubuntu9.1) ...
Errors were encountered while processing:
 grub-efi-amd64-signed
 shim-signed
E: Sub-process /usr/bin/dpkg returned an error code (1)
tom@ubuntu-p7-1380t:~$ 


```

I think I hit this bug:

[https://bugs.launchpad.net/ubuntu/+source/grub2-signed/+bug/1860491](https://bugs.launchpad.net/ubuntu/+source/grub2-signed/+bug/1860491)

So, if grub-efi-signed isn't installed, that explains why the system keeps booting.    What's the best way of dealing with this?

Thanks in advance!

Peace...

---

