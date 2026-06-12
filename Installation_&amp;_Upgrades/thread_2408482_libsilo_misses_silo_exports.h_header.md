---
title: "libsilo misses silo_exports.h header"
date: 2018-12-19
forum: Installation &amp; Upgrades
---

### Post by s-friedemann on 2018-12-19
after installing silo on ubuntu ...
```

sudo apt-get install libsilo-bin  libsilo-dev

```
I get
```

/usr/include/silo.h:75:10: fatal error: silo_exports.h: No such file or directory
 #include <silo_exports.h>
           ^~~~~~~~~~~~~~~~
           compilation terminated.

```
when compiling parflow which depends on silo.


It does not find `silo_exports.h` ! Where can I find this header? is it a packaging problem?


```

/usr$ find . -name '*silo*'
./lib/x86_64-linux-gnu/pkgconfig/silo.pc
./lib/x86_64-linux-gnu/libsiloh5.so
./lib/x86_64-linux-gnu/libsiloh5.so.0.0.0
./lib/x86_64-linux-gnu/libsiloh5.so.0
./share/doc/libsiloh5-0
./share/doc/libsilo-dev
./share/doc/libsilo-bin
./include/silo.h
./include/silo.inc
./bin/silofile
./bin/silodiff
./bin/silock

```
does not help the file seems to not be installed on my system. (Or is there another path where I could search for it?)


My ubuntu version:
```

$ cat /etc/os-release
NAME="Ubuntu"
VERSION="18.04.1 LTS (Bionic Beaver)"
ID=ubuntu
ID_LIKE=debian
PRETTY_NAME="Ubuntu 18.04.1 LTS"
VERSION_ID="18.04"
HOME_URL="https://www.ubuntu.com/"
SUPPORT_URL="https://help.ubuntu.com/"
BUG_REPORT_URL="https://bugs.launchpad.net/ubuntu/"
PRIVACY_POLICY_URL="https://www.ubuntu.com/legal/terms-and-policies/privacy-policy"
VERSION_CODENAME=bionic
UBUNTU_CODENAME=bionic

```

---

