---
title: "can't finish ./compile command"
date: 2011-12-24
forum: Installation &amp; Upgrades
---

### Post by tr4rex on 2011-12-24
I'm using Ubuntu 10.04 with gnome 2.3. g++, gcc, built-essentials are installed. I want to install gtkpod program. The version in the repository is quite old. That's why I decided to build it by myself. I downloaded the archive, unpacked it and changed the folder. When I did the command "./configure" I received the next log
```

******************** // some results
checking for perl >= 5.8.1... 5.10.1
checking for XML::Parser... ok
checking whether ln -s works... yes
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.16... yes
configure: error: glib-compile-schemas not found.

```
Please, help to fix it. I have not found some solution, which I could apply for myself. Thanks in advance.

---

### Post by Shazaam on 2011-12-24
A link...
[https://launchpad.net/ubuntu/+source/gtkpod](https://launchpad.net/ubuntu/+source/gtkpod)

Scroll to the bottom if you want a ppa (personal package archive) that may have newer (untested) versions.

---

