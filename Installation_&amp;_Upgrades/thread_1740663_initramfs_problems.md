---
title: "initramfs problems"
date: 2011-04-27
forum: Installation &amp; Upgrades
---

### Post by blueintegral on 2011-04-27
I'm updating a server that's still running 8.04, and encountered some problems. I ran do-release-upgrade and everything was going fine until near the end. It complained that installArchives() failed. So I ran dpkg --configure -a and got the following:

cpio: ./bin/udevinfo: Cannot stat: No such file or directory
cpio: ./sbin/udevsettle: Cannot stat: No such file or directory
cpio: ./sbin/udevtrigger: Cannot stat: No such file or directory
update-initramfs: failed for /boot/initrd.img-2.6.27-11-server
dpkg: subprocess post-installation script returned error exit status 1

So now, apt-get upgrade doesn't work and I can't upgrade to the next distribution with do-release-upgrade. How can I fix initramfs?

---

### Post by dino99 on 2011-04-27
[https://ubuntugenius.wordpress.com/2010/05/24/fix-a-failed-initramfs-update-do-it-before-you-reboot/](https://ubuntugenius.wordpress.com/2010/05/24/fix-a-failed-initramfs-update-do-it-before-you-reboot/)

[http://www.proposedsolution.com/solutions/ubuntu-booting-to-initramfs-prompt/](http://www.proposedsolution.com/solutions/ubuntu-booting-to-initramfs-prompt/)

---

