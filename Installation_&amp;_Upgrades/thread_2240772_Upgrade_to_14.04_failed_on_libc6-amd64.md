---
title: "Upgrade to 14.04 failed on libc6-amd64"
date: 2014-08-22
forum: Installation &amp; Upgrades
---

### Post by sundman on 2014-08-22
When upgrading a 64-bit server to 14.04 it failed totally in the beginning of the package installation process.

It turned out to be that the installed package **libc6-amd64** that made the upgrade fail.

Uninstalling **libc6-amd64** will render the system completly unusable without any valid dynamic loader.

With the help from [URL="https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=727786" #727786
removal of libc6-amd64 makes system unusable][/URL] the package can be manually removed in a root session (since sudo will break, too):

```

apt-get remove libc6-amd64
cd lib64
/lib/x86_64-linux-gnu/ld-2.17.so /bin/rm ld-linux-x86-64.so.2
/lib/x86_64-linux-gnu/ld-2.17.so /bin/ln -s /lib/x86_64-linux-gnu/ld-2.17.so ld-linux-x86-64.so.2

```

After this, the release-upgrade works as intended.

---

