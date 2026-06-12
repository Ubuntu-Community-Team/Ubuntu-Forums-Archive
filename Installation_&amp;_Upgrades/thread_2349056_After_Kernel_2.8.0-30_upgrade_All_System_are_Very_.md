---
title: "After Kernel 2.8.0-30 upgrade All System are Very Slow"
date: 2017-01-10
forum: Installation &amp; Upgrades
---

### Post by brunocarlomafia on 2017-01-10
Hi,

After I upgrade kernel to version nearly to 2.8.0-30, (2.8.0-32 and 2.8.0-34) all my system are very slow, wify connection, programs, all, anybody have this problem? What I could do to resolve this?

---

### Post by howefield on 2017-01-11
What version of Ubuntu are you using ?

Looks like an end of life version that may have bigger problems that being a bit slow.

---

### Post by brunocarlomafia on 2017-01-11
Hi, no, my ubuntu is 16.10, I install them upgrade to 16.04.

I installed it by upgrading from 16.04

---

### Post by howefield on 2017-01-11
So what is the output of..

```
uname -a
```
```
cat /etc/*-release
```

---

### Post by brunocarlomafia on 2017-01-11
Is this:

```
bruno@bruno-Inspiron:~$ uname -r
4.8.0-30-generic

```

```
bruno@bruno-Inspiron:~$ cat /etc/*-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=16.10
DISTRIB_CODENAME=yakkety
DISTRIB_DESCRIPTION="Ubuntu 16.10"
NAME="Ubuntu"
VERSION="16.10 (Yakkety Yak)"
ID=ubuntu
ID_LIKE=debian
PRETTY_NAME="Ubuntu 16.10"
VERSION_ID="16.10"
HOME_URL="http://www.ubuntu.com/"
SUPPORT_URL="http://help.ubuntu.com/"
BUG_REPORT_URL="http://bugs.launchpad.net/ubuntu/"
PRIVACY_POLICY_URL="http://www.ubuntu.com/legal/terms-and-policies/privacy-policy"
VERSION_CODENAME=yakkety
UBUNTU_CODENAME=yakkety

```

I run kernel 2.8.0-30 because the 32 and 34 cause slow operation... but they are installed here.

My system is always updated.

---

