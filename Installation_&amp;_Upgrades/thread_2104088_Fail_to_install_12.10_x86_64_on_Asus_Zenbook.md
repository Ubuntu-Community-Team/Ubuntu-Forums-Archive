---
title: "Fail to install 12.10 x86_64 on Asus Zenbook"
date: 2013-01-12
forum: Installation &amp; Upgrades
---

### Post by theeverlastinggreed on 2013-01-12
Hi all,

I am trying to install ubuntu over gentoo on my laptop, to no avail. The installer kept crashing with the error 'fail to remove initramfs-tools'. The crash reporter directed me to this crash/bug report: [https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/220961](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/220961)

I am quite certain that I have plenty of disk space. Here is my scheme:
/dev/sda1       50MB    /boot
/dev/sda3       10GB    /
/dev/sda5       10GB    /usr
/dev/sda6         4GB    swap
(I plan on putting home on a separate partition after installation, so there should be more than enough space for everything else)

I also looked through the logs in /var/log/installer. There is only debug, dm and version, and none of them seemed to hold much information.

Any help will be very much appreciated.

---

