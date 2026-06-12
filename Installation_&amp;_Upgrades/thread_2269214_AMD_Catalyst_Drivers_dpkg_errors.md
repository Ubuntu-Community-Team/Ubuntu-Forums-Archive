---
title: "AMD Catalyst Drivers dpkg errors"
date: 2015-03-14
forum: Installation &amp; Upgrades
---

### Post by izlix on 2015-03-14
Hello, I am trying to run Ubuntu on a custom built PC. I would like to install the proprietary driver for my video card (Radeon R9 280) but am having trouble.
I have read many posts about errors encountered when installing these drivers and most of the errors I have read about (as well as encountered and overcome!) have to do with getting the actaul packages to generate.

After running the generator, I try to run the successfully generated packages and receive this error.

> Detected configuration:
Architecture: x86_64 (64-bit)
X Server: X.Org 6.9 or later 64-bit
loki_setup: directory: (null)
Installing package for: Ubuntu/trusty
fglrx_14.200-0ubuntu_.deb
fglrx-amdcccle_14.200-0ubuntu_.deb
fglrx-dev_14.200-0ubuntu_.deb
(Reading database ... 234356 files and directories currently installed.)
Preparing to unpack fglrx_14.200-0ubuntu1_amd64.deb ...
Unpacking fglrx (2:14.200-0ubuntu1) ...
dpkg: error processing archive fglrx_14.200-0ubuntu1_amd64.deb (--install):
 trying to overwrite '/etc/acpi/fglrx-powermode.sh', which is also in package fglrx-core 2:14.501-0ubuntu1
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Selecting previously unselected package fglrx-amdcccle.
Preparing to unpack fglrx-amdcccle_14.200-0ubuntu1_amd64.deb ...
Unpacking fglrx-amdcccle (2:14.200-0ubuntu1) ...
dpkg: dependency problems prevent configuration of fglrx-amdcccle:
 fglrx-amdcccle depends on fglrx; however:
  Package fglrx is not installed.

dpkg: error processing package fglrx-amdcccle (--install):
 dependency problems - leaving unconfigured
Processing triggers for ureadahead (0.100.0-16) ...
Errors were encountered while processing:
 fglrx_14.200-0ubuntu1_amd64.deb
 fglrx-amdcccle
fglrx_14.200-0ubuntu1_amd64.deb fglrx-amdcccle_14.200-0ubuntu1_amd64.deb
Cleaning up removed packages
fglrx_14.200-0ubuntu_.deb
fglrx-amdcccle_14.200-0ubuntu_.deb
fglrx-dev_14.200-0ubuntu_.deb

Any suggestions as to what I should do?

---

### Post by dino99 on 2015-03-14
wonder if trusty has been upgraded to support R280
you better dist-upgrading to Utopic at least, or even better Vivid which is very stable (i'm using it since a few months without trouble at all)

---

### Post by izlix on 2015-03-16
Just to clarify, its the lack of current support for my card and not anything I'm doing incorrectly, yes?
I might try upping to vivid soon. I tried Utopic and it was a disaster... Just recovered back to Trusty lol.

Thanks!

---

