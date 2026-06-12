---
title: "Error! Could not locate dkms.conf file."
date: 2019-04-13
forum: Installation &amp; Upgrades
---

### Post by cosy2 on 2019-04-13
```
Setting up linux-headers-4.15.0-47-generic (4.15.0-47.50) ...
/etc/kernel/header_postinst.d/dkms:
Error! Could not locate dkms.conf file.
File:  does not exist.
run-parts: /etc/kernel/header_postinst.d/dkms exited with return code 4
dpkg: error processing package linux-headers-4.15.0-47-generic (--configure):
 installed linux-headers-4.15.0-47-generic package post-installation script subprocess returned error exit status 1
dpkg: dependency problems prevent configuration of linux-headers-generic:
 linux-headers-generic depends on linux-headers-4.15.0-47-generic; however:
No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                            Package linux-headers-4.15.0-47-generic is not configured yet.

dpkg: error processing package linux-headers-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-headers-generic (= 4.15.0.47.49); however:
  Package linux-headers-generic is not configured yet.

dpkg: error processing package linux-generic (--configure):
 dependency problems - leaving unconfigured
Processing triggers for linux-image-4.15.0-47-generic (4.15.0-47.50) ...
No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                          /etc/kernel/postinst.d/dkms:
Error! Could not locate dkms.conf file.
File:  does not exist.
run-parts: /etc/kernel/postinst.d/dkms exited with return code 4
dpkg: error processing package linux-image-4.15.0-47-generic (--configure):
 installed linux-image-4.15.0-47-generic package post-installation script subprocess returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 linux-headers-4.15.0-47-generic
 linux-headers-generic
 linux-generic
 linux-image-4.15.0-47-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

on a simple update

---

### Post by chlorus on 2019-04-17
I am receiving an identical error - had to boot the prior kernel version (.46) to get a working machine. 
Do you have the Nvidia proprietary drivers installed, by chance? That's the only thing that dkms status lists for me.

---

### Post by cosy2 on 2019-04-19
> **chlorus said:**
> I am receiving an identical error - had to boot the prior kernel version (.46) to get a working machine. 
Do you have the Nvidia proprietary drivers installed, by chance? That's the only thing that dkms status lists for me.

nope no nvidia, was virtual box, rm dkms and virtualbox update and then install dkms and vb again

---

### Post by cosy2 on 2019-08-13
let me bump this again because i got this crap again

---

