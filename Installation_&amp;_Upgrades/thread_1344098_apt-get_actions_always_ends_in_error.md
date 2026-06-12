---
title: "apt-get actions always ends in error"
date: 2009-12-02
forum: Installation &amp; Upgrades
---

### Post by kaspien on 2009-12-02
Apt-get fails every time in runs with the following errors:
> E: linux-image-2.6.31-15-generic: subprocess installed post-installation script returned error exit status 2
E: linux-image-generic: dependency problems - leaving unconfigured
E: linux-generic: dependency problems - leaving unconfigured
E: linux-headers-2.6.31-15-generic: subprocess installed post-installation script returned error exit status 2
E: linux-headers-generic: dependency problems - leaving unconfiguredIt doesn't matter what I was installing, the error still comes up. In fact, the installation for the software will finish just fine, but I'll still see the error above.

How can I fix this?

---

### Post by lloyd_b on 2009-12-02
Try running "sudo apt-get dist-upgrade" - this can resolve dependency issues that just "upgrade" can't.

Lloyd B.

---

### Post by kaspien on 2009-12-02
No such luck :(

> No apport report written because the error message indicates its a followup error from a previous failure.
                                                          Examining /etc/kernel/header_postinst.d.
run-parts: executing /etc/kernel/header_postinst.d/dkms
run-parts: failed to exec /etc/kernel/header_postinst.d/dkms: Exec format error
run-parts: /etc/kernel/header_postinst.d/dkms exited with return code 1
Failed to process /etc/kernel/header_postinst.d at /var/lib/dpkg/info/linux-headers-2.6.31-15-generic.postinst line 110.
dpkg: error processing linux-headers-2.6.31-15-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of linux-headers-generic:
 linux-headers-generic depends on linux-headers-2.6.31-15-generic; however:
  Package linux-headers-2.6.31-15-generic is not configured yet.
dpkg: error processing linux-headers-generic (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 linux-image-2.6.31-15-generic
 linux-image-generic
 linux-generic
 linux-headers-2.6.31-15-generic
 linux-headers-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)

Anything else I can try?

---

### Post by wojox on 2009-12-02
After you get that error, try apt-get -f install to force an install of the files that didn't get loaded because of the error. Then try apt-get upgrade again, apt-get -f install back and forth until only the package that has the error is left.

---

