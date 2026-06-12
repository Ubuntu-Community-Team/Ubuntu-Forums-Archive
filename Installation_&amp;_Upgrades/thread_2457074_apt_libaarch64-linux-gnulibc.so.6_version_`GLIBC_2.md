---
title: "apt: /lib/aarch64-linux-gnu/libc.so.6: version `GLIBC_2.27' not found (required by /u"
date: 2021-01-25
forum: Installation &amp; Upgrades
---

### Post by marietto2008 on 2021-01-25
I think that I did an huge mistake trying to install the wrong libc6 package on my ubuntu 18.04 (arm64) installed on my jetson nano because now the os is not working at all anymore and I don't know how to fix that.

```
root@ziomario-desktop:~/Scaricati/arm64# dpkg -i libc6_2.24-11+deb9u4_arm64.deb

dpkg: attenzione: downgrade of libc6:arm64 from version 2.27-3ubuntu1.4 to 2.24-11+deb9u4
(reading from database... 323470 file e directory actually installed.)
Preparing for extracting libc6_2.24-11+deb9u4_arm64.deb...
De-configuration of libc6:armhf (2.27-3ubuntu1.4)...
Extraction of libc6:arm64 (2.24-11+deb9u4) su (2.27-3ubuntu1.4)...
dpkg: error trying to process package libc6:arm64 (--install):
 package libc6:arm64 2.24-11+deb9u4 can't be configured why libc6:armhf has a different version (2.27-3ubuntu1.4)
dpkg: error trying to elaborate package libc6:armhf (--install):
 package libc6:armhf 2.27-3ubuntu1.4 can't be configured why libc6:arm64 has a different version (2.24-11+deb9u4)
Occurred some errors during the processing of :
 libc6:arm64
 libc6:armhf

root@ziomario-desktop:/home# apt update

apt: /lib/aarch64-linux-gnu/libc.so.6: version `GLIBC_2.27' not found (required by /usr/lib/aarch64-linux-gnu/libapt-pkg.so.5.0)
apt: /lib/aarch64-linux-gnu/libc.so.6: version `GLIBC_2.25' not found (required by /lib/aarch64-linux-gnu/libudev.so.1)
apt: /lib/aarch64-linux-gnu/libc.so.6: version `GLIBC_2.25' not found (required by /lib/aarch64-linux-gnu/libsystemd.so.0)
apt: /lib/aarch64-linux-gnu/libc.so.6: version `GLIBC_2.27' not found (required by /lib/aarch64-linux-gnu/libsystemd.so.0)

sudo dpkg --remove-architecture armhf
cannot remove it because it is currently in use by the database
```

Basically i can't do anything and I suspect that if I reboot the board,ubuntu will not restart correctly. So,I'm forced to keep the board up a running until I fix the error. For sure i don't want to reinstall ubuntu from scratch. Please help me. thanks.

---

### Post by marietto2008 on 2021-01-25
fixed with : dpkg -i --force-overwrite libc6_2.27-3ubuntu1.4_arm64.deb

---

