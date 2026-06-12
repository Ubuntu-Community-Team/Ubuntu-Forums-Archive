---
title: "feisty upgrade problem"
date: 2007-04-20
forum: Installation &amp; Upgrades
---

### Post by mitjab on 2007-04-20
```

Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages will be upgraded:
  ttf-dejavu
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/3442kB of archives.
After unpacking 598kB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 66947 files and directories currently installed.)
Preparing to replace ttf-dejavu 2.7-2 (using .../ttf-dejavu_2.14-2_all.deb) ...
Unpacking replacement ttf-dejavu ...

dpkg-deb (subprocess): error in buffer_read(stream): failed to write to pipe in copy: Input/output error
dpkg-deb: subprocess paste returned error exit status 2
dpkg: error processing /var/cache/apt/archives/ttf-dejavu_2.14-2_all.deb (--unpack):
 short read in buffer_copy (backend dpkg-deb during `./usr/share/fonts/truetype/ttf-dejavu/DejaVuSerifCondensed.ttf')
Errors were encountered while processing:
 /var/cache/apt/archives/ttf-dejavu_2.14-2_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

how to fix this?

---

### Post by mitjab on 2007-04-20
fiexd!

---

