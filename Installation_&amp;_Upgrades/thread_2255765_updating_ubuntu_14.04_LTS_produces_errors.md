---
title: "updating ubuntu 14.04 LTS produces errors"
date: 2014-12-07
forum: Installation &amp; Upgrades
---

### Post by John_Carnazzo on 2014-12-07
Hello,

I have a reoccuring error when trying to get an update for my Ubuntu 14.04.1 LTS the message is:

Processing triggers for initramfs-tools (0.103ubuntu4.2) ...
update-initramfs: Generating /boot/initrd.img-3.13.0-39-generic

gzip: stdout: No space left on device
E: mkinitramfs failure cpio 141 gzip 1
update-initramfs: failed for /boot/initrd.img-3.13.0-39-generic with 1.
dpkg: error processing package initramfs-tools (--configure):
 subprocess installed post-installation script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 linux-image-3.13.0-40-generic
 linux-image-extra-3.13.0-40-generic
 linux-image-generic
 linux-generic
 initramfs-tools
E: Sub-process /usr/bin/dpkg returned an error code (1)

I would like to figure this out and any help would be appreciated

John

---

### Post by steeldriver on 2014-12-07
The key part is likely

```

gzip: stdout: **No space left on device**

```

Is your root partition (or your /boot partition, if you have a separate one) full? you can check with

```

df -h

```

---

### Post by John_Carnazzo on 2014-12-14
Thank you I resolved the problem and do not recieve the error message any more.

---

