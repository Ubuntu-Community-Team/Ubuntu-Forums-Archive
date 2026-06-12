---
title: "installing wxWidgets 2.8.7 for nightly builds of code blocks"
date: 2007-12-06
forum: Installation &amp; Upgrades
---

### Post by kthakore on 2007-12-06
I am trying to install the latest nightly build of code blocks but when I try to install it I get

```

libcodeblocks0: Depends: libwxgtk2.8-0 (>= 2.8.7) but 2.8.4.0-0ubuntu3 is to be installed
E: Broken packages

```
not sure where I can find this lib I downloaded** [wxAll ]("http://www.wxwidgets.org/downloads/")** because the ubuntu package document site for **[libwxgtk2.8-0 2.8.4]("http://packages.ubuntu.com/gutsy/libs/libwxgtk2.8-0")** said it was located in wxAll.

I compiled the wxWidgets with ./configure --with-gtk --enable-shared (to ensure gtk was included and shared libraries were compiled) them I ran make install with no problems. but when I tried to install libcodeblocks0 again I got the same error as above.

---

### Post by kthakore on 2007-12-06
what am I doing wrong?

---

### Post by kthakore on 2007-12-07
shame less bump

---

### Post by Yumb on 2007-12-14
Anyone?

---

### Post by Envy Geek on 2007-12-17
I don't know why compiling it doesn't work, but this page,  [http://wiki.wxpython.org/InstallingOnUbuntuOrDebian]("http://wiki.wxpython.org/InstallingOnUbuntuOrDebian"), explains how to install the newest wx for Ubuntu. It allowed me, at least, to install the latest codeblocks.
hope this helps

Anthony

---

