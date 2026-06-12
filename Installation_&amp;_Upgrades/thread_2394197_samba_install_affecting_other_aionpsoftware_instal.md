---
title: "samba install affecting other aionp/software installat"
date: 2018-06-13
forum: Installation &amp; Upgrades
---

### Post by irvenkapata on 2018-06-13
I am getting the following errors during samba installation.
 please asist.

#################################################below ###################################################

```
Processing triggers for man-db (2.8.3-2) ...
Setting up samba-common-bin (2:4.8.2+dfsg-1) ...
Checking smb.conf
ERROR: Unable to load default file
dpkg: error processing package samba-common-bin (--configure):
 installed samba-common-bin package post-installation script subprocess returned error exit status 255
dpkg: dependency problems prevent configuration of samba:
 samba depends on samba-common-bin (= 2:4.8.2+dfsg-1); however:
  Package samba-common-bin is not configured yet.

dpkg: error processing package samba (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          Errors were encountered while processing:
 samba-common-bin
 samba
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

