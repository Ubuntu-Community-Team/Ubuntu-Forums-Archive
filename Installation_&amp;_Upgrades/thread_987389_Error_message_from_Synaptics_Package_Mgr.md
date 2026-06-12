---
title: "Error message from Synaptics Package Mgr"
date: 2008-11-19
forum: Installation &amp; Upgrades
---

### Post by subseashaun on 2008-11-19
Guys, just tried an updated using Syn Pack Mgr and this came up:

W: GPG error: [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>


I can see its invalid signatures but what do I do to get it to update?

Any help appreciated, I'm still a bit of a newbie LOL

Shaun.

---

### Post by pennacook on 2008-11-19
I found on launchpad that you can run:

```
$ sudo apt-get update -o Acquire::http::No-Cache=true
```

---

