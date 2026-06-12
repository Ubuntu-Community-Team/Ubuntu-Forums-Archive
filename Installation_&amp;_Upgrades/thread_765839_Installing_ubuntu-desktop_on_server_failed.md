---
title: "Installing ubuntu-desktop on server failed"
date: 2008-04-24
forum: Installation &amp; Upgrades
---

### Post by austin1030 on 2008-04-24
When I try to installing ubuntu-desktop on Ubuntu 8.04 server, it gave me an error on python-gnome2.

```
dkpg: parse error, in file '/var/lib/dpkg/status' near line 275 package 'python-gnome2';
'Depends' field, invalid package name 'E: Sub-process /usr/bin/dpkg returned an error code (2)
```

Does any one has same problem? I'm gonna try to install again.

BTW, it took forever to download ubuntu-desktop and install it. I guess there are just too many people downloading same desktop gui.

Austin

---

### Post by hytek on 2008-04-25
I can't even get ubuntu-desktop installed on 8.04 amd64 server.

Keeps timing out on
0% [Connecting to us.archive.ubuntu.com (91.189.92.3)]

Even when trying an apt-get update it fails on this particular repository.

If I ping this IP, I get 0% packet loss of around 100 packets. So I don't think it is a bandwidth issue.

---

### Post by austin1030 on 2008-04-25
yeah, that is what happending to me. Becuase of that it takes forever to install anything.

Austin

---

### Post by hytek on 2008-04-25
austin, try this. It is working for me to get the packages, albeit really slow :(

$apt-get install ubuntu-desktop --fix-missing

---

### Post by hytek on 2008-04-25
--fix-mising doesn't work either.

Can someone take a look at this repository please?

Seems there might be a problem

Cheers.

---

### Post by zvacet on 2008-04-25
You can try replace us.archive.ubuntu.com with archive.ubuntu.com in your source list,but servers are very busy these days,because everyone want new release first day.Like it is limited numbers of new release.Try anyway and good luck!

---

