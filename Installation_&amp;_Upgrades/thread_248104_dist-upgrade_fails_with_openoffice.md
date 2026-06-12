---
title: "dist-upgrade fails with openoffice"
date: 2006-08-31
forum: Installation &amp; Upgrades
---

### Post by chadk on 2006-08-31
```

20 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
9 not fully installed or removed.
Need to get 0B/89.8MB of archives.
After unpacking 26.9MB of additional disk space will be used.
Do you want to continue [Y/n]? Y
(Reading database ... 158456 files and directories currently installed.)
Preparing to replace openoffice.org-calc 2.0.2-2ubuntu12.1 (using .../openoffice.org-calc_2.0.3-3ubuntu1_i386.deb) ...
Unpacking replacement openoffice.org-calc ...
dpkg: error processing /var/cache/apt/archives/openoffice.org-calc_2.0.3-3ubuntu1_i386.deb (--unpack):
 trying to overwrite `/usr/lib/openoffice/help/en/scalc.idx/DICTIONARY', which is also in package openoffice.org-help-en-us
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Preparing to replace openoffice.org-writer 2.0.2-2ubuntu12.1 (using .../openoffice.org-writer_2.0.3-3ubuntu1_i386.deb) ...
Unpacking replacement openoffice.org-writer ...
dpkg: error processing /var/cache/apt/archives/openoffice.org-writer_2.0.3-3ubuntu1_i386.deb (--unpack):
 trying to overwrite `/usr/lib/openoffice/help/en/swriter.idx/DICTIONARY', which is also in package openoffice.org-help-en-us
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Preparing to replace openoffice.org-draw 2.0.2-2ubuntu12.1 (using .../openoffice.org-draw_2.0.3-3ubuntu1_i386.deb) ...
Unpacking replacement openoffice.org-draw ...
dpkg: error processing /var/cache/apt/archives/openoffice.org-draw_2.0.3-3ubuntu1_i386.deb (--unpack):
 trying to overwrite `/usr/lib/openoffice/help/en/sdraw.idx/DICTIONARY', which is also in package openoffice.org-help-en-us
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Preparing to replace openoffice.org-impress 2.0.2-2ubuntu12.1 (using .../openoffice.org-impress_2.0.3-3ubuntu1_i386.deb) ...
Unpacking replacement openoffice.org-impress ...
dpkg: error processing /var/cache/apt/archives/openoffice.org-impress_2.0.3-3ubuntu1_i386.deb (--unpack):
 trying to overwrite `/usr/lib/openoffice/help/en/simpress.idx/DICTIONARY', which is also in package openoffice.org-help-en-us
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Preparing to replace openoffice.org-math 2.0.2-2ubuntu12.1 (using .../openoffice.org-math_2.0.3-3ubuntu1_i386.deb) ...
Unpacking replacement openoffice.org-math ...
dpkg: error processing /var/cache/apt/archives/openoffice.org-math_2.0.3-3ubuntu1_i386.deb (--unpack):
 trying to overwrite `/usr/lib/openoffice/help/en/smath.idx/DICTIONARY', which is also in package openoffice.org-help-en-us
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Preparing to replace openoffice.org-base 2.0.2-2ubuntu12.1 (using .../openoffice.org-base_2.0.3-3ubuntu1_i386.deb) ...
Unpacking replacement openoffice.org-base ...
dpkg: error processing /var/cache/apt/archives/openoffice.org-base_2.0.3-3ubuntu1_i386.deb (--unpack):
 trying to overwrite `/usr/lib/openoffice/help/en/sdatabase.idx/DICTIONARY', which is also in package openoffice.org-help-en-us
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/openoffice.org-calc_2.0.3-3ubuntu1_i386.deb
 /var/cache/apt/archives/openoffice.org-writer_2.0.3-3ubuntu1_i386.deb
 /var/cache/apt/archives/openoffice.org-draw_2.0.3-3ubuntu1_i386.deb
 /var/cache/apt/archives/openoffice.org-impress_2.0.3-3ubuntu1_i386.deb
 /var/cache/apt/archives/openoffice.org-math_2.0.3-3ubuntu1_i386.deb
 /var/cache/apt/archives/openoffice.org-base_2.0.3-3ubuntu1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Not sure what's going on with this.

---

### Post by aschiller on 2006-08-31
I'm having the same problem.

---

### Post by chadk on 2006-09-01
Well today it reports I'm up to date and there are no updates so whatever.

---

