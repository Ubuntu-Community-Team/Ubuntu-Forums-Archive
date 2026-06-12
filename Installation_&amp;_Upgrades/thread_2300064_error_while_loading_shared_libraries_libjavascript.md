---
title: "error while loading shared libraries: libjavascriptcoregtk-3.0.so.0"
date: 2015-10-23
forum: Installation &amp; Upgrades
---

### Post by xaver-s on 2015-10-23
Hi,
When trying to start the software-center or rhythmbox i get the following error:

```
rhythmbox: error while loading shared libraries: libjavascriptcoregtk-3.0.so.0: cannot open shared object file: No such file or directory
```

It first happened after installing the Ubuntu Component Store from their PPA.
I already reinstalled rhythmbox, libjavascriptcoregtk-3.0 and libwebkitgtk-3.0 and removed the Ubuntu Component Store again but I still get the error.

OS: Ubuntu 14.04 LTS

---

### Post by xaver-s on 2015-10-24
I was able to solve the problem by installing the package manually after downloading it from: [http://packages.ubuntu.com/precise/libs/libjavascriptcoregtk-3.0-0](http://packages.ubuntu.com/precise/libs/libjavascriptcoregtk-3.0-0)
After installing I ran
```
sudo apt-get update
sudo apt-get -f upgrade
```

The package was then automatically reinstalled from the official packages and worked again, although just removing the package and installing it again had not worked before.

---

