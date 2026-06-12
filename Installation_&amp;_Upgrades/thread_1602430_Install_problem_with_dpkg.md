---
title: "Install problem with dpkg"
date: 2010-10-21
forum: Installation &amp; Upgrades
---

### Post by ubuaverill on 2010-10-21
Can someone help me with this app install problem: I am attempting to  install 'Motion', a video capture program. The installation fails with  this error:

installArchives() failed: dpkg: parse error, in file '/var/lib/dpkg/available' near line 43386 package 'libpng12-0': 
 `Replaces' field, reference to `libpng12-dev': error in version: epoch in version is not number

A fix for this problem is greatly appreciated.

---

### Post by gmargo on 2010-10-21
The file /var/lib/dpkg/available is a text file so take a look at that line in the file and see if anything looks corrupted.

Here's what it should look like on 10.10 maverick:
```

Package: libpng12-0
Priority: optional
Section: libs
Installed-Size: 324
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: i386
Source: libpng
Version: 1.2.44-1
Replaces: libpng12-dev (<= 1.2.8rel-7)
Depends: libc6 (>= 2.11), zlib1g (>= 1:1.1.4)
Conflicts: libpng12-dev (<= 1.2.8rel-7), mzscheme (<= 1:209-5), pngcrush (<= 1.5.10-2), pngmeta (<= 1.11-3), povray-3.5 (<= 3.5.0c-10), qemacs (<= 0.3.1-5)
Filename: pool/main/libp/libpng/libpng12-0_1.2.42-1ubuntu2_i386.deb
Size: 176906
MD5sum: c8fc720bb566b1a19cf5db9d8aa2a9f2
Description: PNG library - runtime
 libpng is a library implementing an interface for reading and writing
 PNG (Portable Network Graphics) format files.
 .
 This package contains the runtime library files needed to run software
 using libpng.
Original-Maintainer: Anibal Monsalve Salazar <anibal@debian.org>
Homepage: http://libpng.org/pub/png/libpng.html


```

---

### Post by sikander3786 on 2010-10-21
You can also clear the contents of the file and they should be regenerated automatically thereafter.

```
sudo dpkg --clear-avail
```

---

### Post by ubuaverill on 2010-10-21
Sikander...
Thank you for your help, particularly the apt-get --clear-avail suggestion because it is a more general solution.

---

### Post by sikander3786 on 2010-10-21
> **ubuaverill said:**
> Sikander...
Thank you for your help, particularly the apt-get --clear-avail suggestion because it is a more general solution.
You are welcome :-) Is it solved now? If solved, please mark it solved using 'Thread Tools' near the top right of this page.

Happy Ubuntu-ing!

---

### Post by oregonbob on 2010-10-21
This may be drift, but thanks for the tip on the program "motion". That was just what I have been looking for. I have numerous netcams set up and was looking for better solution to capture only action. I installed that motion package, added my first netcam's URL and it worked first test!

---

