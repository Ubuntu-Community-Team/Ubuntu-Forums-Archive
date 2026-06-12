---
title: "wubi error"
date: 2012-10-17
forum: Installation &amp; Upgrades
---

### Post by coliny on 2012-10-17
Ran the wubi installation on dell 1018 netbook w7 it completed the download without problem but then gave error 'could not retreive required installation files'. In the wubi log file at the second distro entry it says does not contain C:\.......\pyld51b.tmp\casper\filesystem\squashfs

---

### Post by bcbc on 2012-10-17
I don't think that's the relevant line. Please either post the entire log or look near the end for the error (not necessarily the last error)

PS if you're installing lubuntu 12.04 then there is a problem with the version of Wubi you have. It assumes that the ISO is release 12.04.1 and there is no lubuntu 12.04.1 ISO. That's because Wubi.exe is release specific and it has been bumped to 12.04.1 - so it no longer accepts any 12.04 ISO.

So you will have to use the 12.04 wubi.exe (from here: [http://people.canonical.com/~evand/wubi/precise/wubi-r266-signed.exe](http://people.canonical.com/~evand/wubi/precise/wubi-r266-signed.exe)). You don't need to rename it - just run it like that and it will work for lubuntu (only lubuntu, not ubuntu or other flavours like kubuntu etc.).

PPS here's the bug report (feel free to clicking on This affects me): [https://bugs.launchpad.net/wubi/+bug/1043607](https://bugs.launchpad.net/wubi/+bug/1043607)

---

### Post by coliny on 2012-10-19
:) problem solved. installation was to C:\ but part way down log file it tried to use Q:\. Q:\ was created bt microsoft click-to-run office & locked. Uninstalled this app in w7 to remove Q:\ & then wubi succeeded.

Thanks for your help.

---

### Post by bcbc on 2012-10-19
> **coliny said:**
> :) problem solved. installation was to C:\ but part way down log file it tried to use Q:\. Q:\ was created bt microsoft click-to-run office & locked. Uninstalled this app in w7 to remove Q:\ & then wubi succeeded.

Thanks for your help.

This should not have been necessary. There used to be a bug when the presence of the micrsoft click-to-run drive was present (and other virtual drives), but it was not required to remove it. And that was fixed with bug [lpbug]862003[/lpbug].

So please if you can, post the wubi log file here.

---

