---
title: "Update stalls on &quot;update-initramfs: Generating /boot/initrd.img-4.4.0-63-generic&quot;"
date: 2017-02-23
forum: Installation &amp; Upgrades
---

### Post by tbenst on 2017-02-23
I am unable to get `sudo apt-get upgrade` to complete on Ubuntu 16.04.

```

Fetched 1,571 MB in 2min 9s (12.2 MB/s)                                                 
Extracting templates from packages: 100%
Preconfiguring packages ...
(Reading database ... 344634 files and directories currently installed.)
Preparing to unpack .../base-files_9.4ubuntu4.4_amd64.deb ...
Unpacking base-files (9.4ubuntu4.4) over (9.4ubuntu4.3) ...
Processing triggers for plymouth-theme-ubuntu-text (0.9.2-3ubuntu13.1) ...
update-initramfs: deferring update (trigger activated)
Processing triggers for man-db (2.7.5-1) ...
Processing triggers for cracklib-runtime (2.9.2-1build2) ...
Processing triggers for install-info (6.1.0.dfsg.1-5) ...
Processing triggers for initramfs-tools (0.122ubuntu8.8) ...
update-initramfs: Generating /boot/initrd.img-4.4.0-63-generic

```

Any thoughts or anyone else seeing this? Killing and restarting does not help

---

