---
title: "MD5SUMS does not match md5sum for wubi.exe"
date: 2008-04-25
forum: Installation &amp; Upgrades
---

### Post by djbristow on 2008-04-25
I have downloaded several copies of WUBI.EXE from sites:

ftp.funet.fi
ftp.ussg.iu.edu
mirrors.kernel.org
releases.ubuntu.com
even the copy that is in the desktop i386 ISO (the ISO md5sum matches)

They all without exception generate a md5sum of:

a96aa69961f3ed80dd7a88fae1e28196  wubi.exe

The MD5SUMS file from releases.ubuntu.com shows the md5sum for this file as:

cdd32124f23b455b0aa22cc3ff35ff35 *wubi.exe

I have made sure to download in binary mode.  I have used several FTP clients which default to binary mode (for example, ncftp, lftp).

Is it possible that the MD5SUMS file is wrong?

---

