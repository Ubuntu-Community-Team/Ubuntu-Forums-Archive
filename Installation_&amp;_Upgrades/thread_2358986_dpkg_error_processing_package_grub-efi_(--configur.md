---
title: "dpkg: error processing package grub-efi (--configure):"
date: 2017-04-19
forum: Installation &amp; Upgrades
---

### Post by matheusbnas on 2017-04-19
```
matheusb@matheusb-Lenovo-G40-80:~$ sudo apt -f installReading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
2 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Setting up grub-efi-amd64 (2.02~beta2-36ubuntu3.9) ...
dpkg: error processing package grub-efi-amd64 (--configure):
 subprocess installed post-installation script returned error exit status 10
dpkg: dependency problems prevent configuration of grub-efi:
 grub-efi depends on grub-efi-amd64 (= 2.02~beta2-36ubuntu3.9); however:
  Package grub-efi-amd64 is not configured yet.


dpkg: error processing package grub-efi (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                          Errors were encountered while processing:
 grub-efi-amd64
 grub-efi
E: Sub-process /usr/bin/dpkg returned an error code (1)



```

---

### Post by oldfred on 2017-04-19
May be best to see details, you can run from Ubuntu live installer or any working install:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) and:
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

