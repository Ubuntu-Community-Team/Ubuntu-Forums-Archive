---
title: "'libgssapi-krb5-2' problem killing all installs"
date: 2010-02-19
forum: Installation &amp; Upgrades
---

### Post by geekchicohio on 2010-02-19
Hey all,
I'm currently running a brand-new (this morning) install of 9.10 and I'm running into a problem with apt.
Any attempts at installing anything via apt-get or via downloaded .deb files is producing the following:
```

Fetched 17.6MB in 1min 28s (199kB/s)                                           
Extracting templates from packages: 100%
Selecting previously deselected package liba52-0.7.4.
(Reading database ... 10%dpkg: unrecoverable fatal error, aborting:
 files list file for package `libgssapi-krb5-2' contains empty filename
E: Sub-process /usr/bin/dpkg returned an error code (2)

```

I'm by no means a Linux ninja, but I've been running Ubuntu exclusively since 6.06 so I've got a lot of experience in following directions from you fine folks.
Any and all help will be greatly appreciated.

---

### Post by geekchicohio on 2010-02-19
This problem, which I've learned was a dpkg problem, has been fixed.
I followed the steps listed in this thread:

[http://ubuntuforums.org/showthread.php?t=1301928&highlight=empty+filename](http://ubuntuforums.org/showthread.php?t=1301928&highlight=empty+filename)

and replaced the filename listed, with the filename that was giving me trouble (libgssapi-krb5-2)

---

