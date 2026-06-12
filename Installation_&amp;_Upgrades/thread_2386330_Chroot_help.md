---
title: "Chroot help"
date: 2018-03-04
forum: Installation &amp; Upgrades
---

### Post by warmango on 2018-03-04
so I'm setting up Ubuntu Xenial (armhf), and the way I'm doing it is using "Linux Deploy" on my rooted phone (galaxy s5 g900t). But it fails to get the packages listed below and install them...

```
apt apt-utils base-passwd 
bsdmainutils bsdutils bzip2 console-setup 
console-setup-linux cron dash debconf dh-python
 file findutils gcc-5-base gnupg hostname 
initramfs-tools libacl1 libbsd0 libbz2-1.0 
libcryptsetup4 libffi6 libgdbm3 libgmp10 
libgnutls-openssl27 libgpg-error0 
libhogweed4 libidn11 liblocale-gettext-perl 
liblzma5 libmnl0 libncurses5 libncursesw5 
libnewt0.52 libp11-kit0 libpam-modules-bin 
libpcre3 libpopt0 libsepol1 libsqlite3-0 libss2
 libustr-1.0-1 locales login lsb-release 
makedev mawk net-tools procps python3 
python3-minimal python3.5-minimal 
readline-common sensible-utils systemd-sysv 
tar ubuntu-keyring ucf util-linux
 vim-tiny
```


Where can I get these directly?

---

### Post by warmango on 2018-03-06
Bump?

---

### Post by mg2003 on 2018-03-06
Maybe try adding or changing repositories?
[https://help.ubuntu.com/community/Repositories/CommandLine](https://help.ubuntu.com/community/Repositories/CommandLine)

I mean, you can still technically google each one and add them one by one like this:
[https://packages.ubuntu.com/trusty/utils/bsdmainutils](https://packages.ubuntu.com/trusty/utils/bsdmainutils)

---

