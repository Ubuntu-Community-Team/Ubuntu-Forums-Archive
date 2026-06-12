---
title: "404 Errors from Canonical Server on Updates ..."
date: 2013-11-27
forum: Installation &amp; Upgrades
---

### Post by vdeepakkumar on 2013-11-27
A few of the updates are failing in Muan Update Manager with the following error. 

Failed to download [http://us.archive.ubuntu.com/ubuntu/pool/main/i/initramfs-tools/initramfs-tools_0.99ubuntu13.3_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/i/initramfs-tools/initramfs-tools_0.99ubuntu13.3_all.deb)
 404  Not Found [IP: 91.189.91.15 80]
 

 Failed to download [http://us.archive.ubuntu.com/ubuntu/pool/main/i/initramfs-tools/initramfs-tools-bin_0.99ubuntu13.3_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/i/initramfs-tools/initramfs-tools-bin_0.99ubuntu13.3_i386.deb)
 404  Not Found [IP: 91.189.91.15 80]

---

### Post by oldos2er on 2013-11-27
[http://us.archive.ubuntu.com/ubuntu/pool/main/i/initramfs-tools/initramfs-tools_0.99ubuntu13.4_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/i/initramfs-tools/initramfs-tools_0.99ubuntu13.4_all.deb) is there. Have you tried running ```
sudo apt-get update && sudo apt-get dist-upgrade
``` ?

---

