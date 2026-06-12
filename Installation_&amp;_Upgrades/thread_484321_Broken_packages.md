---
title: "Broken packages"
date: 2007-06-25
forum: Installation &amp; Upgrades
---

### Post by dfein99 on 2007-06-25
Hi all,
I'm trying to install mplayer but getting the following:

[INDENT]The following packages have unmet dependencies:
  mplayer: Depends: libdvdread3 (>= 0.9.6) but it is not installable
           Depends: libggi2 (>= 1:2.2.1) but it is not installable
E: Broken packages[/INDENT]

when I try to update the package I get this (I'm not sure if this is the cause)
[INDENT]Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Packages [4912kB]
99% [6 Packages gzip 0]
gzip: stdin: not in gzip format
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Packages
  Sub-process gzip returned an error code (1)
Fetched 6B in 1s (4B/s)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-i386/Packages.gz)  Sub-process gzip returned an error code (1) 
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.
 [/INDENT]

I also tried to install the libdvdread3 separately but with out sucsses.
Thank in advance ,

---

