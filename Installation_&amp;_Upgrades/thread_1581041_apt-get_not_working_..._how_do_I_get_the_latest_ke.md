---
title: "apt-get not working ... how do I get the latest kernel upgrade?"
date: 2010-09-24
forum: Installation &amp; Upgrades
---

### Post by Skaperen on 2010-09-24
I know the new kernel is available, according to the web site.  But, as seen here, the documented apt-get commands are not working.  Should I switch over to using something else like "aptitude" instead, if "apt-get" won't work?

```
meitner/root/x0 /root 56# apt-get update
Hit http://security.ubuntu.com karmic-security Release.gpg
Ign http://security.ubuntu.com karmic-security/main Translation-en_US
Hit http://us.archive.ubuntu.com karmic Release.gpg
Ign http://us.archive.ubuntu.com karmic/main Translation-en_US
Ign http://security.ubuntu.com karmic-security/restricted Translation-en_US
Ign http://security.ubuntu.com karmic-security/universe Translation-en_US
Ign http://security.ubuntu.com karmic-security/multiverse Translation-en_US
Hit http://security.ubuntu.com karmic-security Release
Ign http://us.archive.ubuntu.com karmic/restricted Translation-en_US
Ign http://us.archive.ubuntu.com karmic/universe Translation-en_US
Ign http://us.archive.ubuntu.com karmic/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com karmic-updates Release.gpg
Ign http://us.archive.ubuntu.com karmic-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com karmic-updates/restricted Translation-en_US
Ign http://us.archive.ubuntu.com karmic-updates/universe Translation-en_US
Ign http://us.archive.ubuntu.com karmic-updates/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com karmic Release
Hit http://us.archive.ubuntu.com karmic-updates Release
Hit http://us.archive.ubuntu.com karmic/main Packages
Hit http://us.archive.ubuntu.com karmic/restricted Packages
Hit http://us.archive.ubuntu.com karmic/main Sources
Hit http://us.archive.ubuntu.com karmic/restricted Sources
Hit http://us.archive.ubuntu.com karmic/universe Packages
Hit http://us.archive.ubuntu.com karmic/universe Sources
Hit http://us.archive.ubuntu.com karmic/multiverse Packages
Hit http://us.archive.ubuntu.com karmic/multiverse Sources
Hit http://security.ubuntu.com karmic-security/main Packages
Hit http://security.ubuntu.com karmic-security/restricted Packages
Hit http://security.ubuntu.com karmic-security/main Sources
Hit http://security.ubuntu.com karmic-security/restricted Sources
Hit http://security.ubuntu.com karmic-security/universe Packages
Hit http://security.ubuntu.com karmic-security/universe Sources
Hit http://us.archive.ubuntu.com karmic-updates/main Packages
Hit http://us.archive.ubuntu.com karmic-updates/restricted Packages
Hit http://us.archive.ubuntu.com karmic-updates/main Sources
Hit http://security.ubuntu.com karmic-security/multiverse Packages
Hit http://security.ubuntu.com karmic-security/multiverse Sources
Hit http://us.archive.ubuntu.com karmic-updates/restricted Sources
Hit http://us.archive.ubuntu.com karmic-updates/universe Packages
Hit http://us.archive.ubuntu.com karmic-updates/universe Sources
Hit http://us.archive.ubuntu.com karmic-updates/multiverse Packages
Hit http://us.archive.ubuntu.com karmic-updates/multiverse Sources
Reading package lists... Done
meitner/root/x0 /root 57# dpkg -l | grep linux
ii  libselinux1                       2.0.85-2ubuntu2                   SELinux shared libraries
ii  libv4l-0                          0.6.0-1                           Collection of video4linux support libraries
ii  linux-firmware                    1.26                              Firmware for Linux kernel drivers
ii  linux-image-2.6.31-14-server      2.6.31-14.48                      Linux kernel image for version 2.6.31 on x86
ii  util-linux                        2.16-1ubuntu5                     Miscellaneous system utilities
meitner/root/x0 /root 58# apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
meitner/root/x0 /root 59# 
```

---

### Post by akoskm on 2010-09-24
Have you tried to update simple with:
```

sudo apt-get upgrade

```?

---

### Post by Bachstelze on 2010-09-24
> **Skaperen said:**
> I know the new kernel is available, according to the web site.

Which web site?

---

### Post by ptn107 on 2010-09-24
Make sure the following packages are installed, if not install them:

linux-server
linux-generic-pae
linux-image-generic-pae
linux-image-2.6.31-22-generic-pae
linux-image-server
linux-image-2.6.31-22-server

---

### Post by Skaperen on 2010-09-24
> **akoskm said:**
> Have you tried to update simple with:
```

sudo apt-get upgrade

```?
That's what I first tried.

---

### Post by Skaperen on 2010-09-24
> **ptn107 said:**
> Make sure the following packages are installed, if not install them:

linux-server
linux-generic-pae
linux-image-generic-pae
linux-image-2.6.31-22-generic-pae
linux-image-server
linux-image-2.6.31-22-server
1.  The kernel doesn't automatically upgrade anymore?

2.  Does PAE make sense?  This is a 64-bit system, where the latest kernel exploit is an issue.

---

### Post by Skaperen on 2010-09-24
> **Bachstelze said:**
> Which web site?
[http://www.ubuntu.com/usn/usn-988-1](http://www.ubuntu.com/usn/usn-988-1)

---

