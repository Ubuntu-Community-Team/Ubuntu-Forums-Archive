---
title: "Need X11 Developer Headers... but where?"
date: 2005-03-16
forum: Installation &amp; Upgrades
---

### Post by obelix on 2005-03-16
I did a custom install because I have a super old P200 which only needs command Line access. I'm in the midst of compiling a program I need to use and it gives me this error:

Please install the X11 developer headers for your platform
configure: error Broken X11 install. No X11 headers.

Now obviously I don't have X installed but I'm wondering what is the minimum set of packages I need to download through apt-get in order to get this to work? I tried apt-get install X11 and apt-get install X11-dev and it can't find any packages. 

Any help would be very much appreciated.

---

### Post by daniels on 2005-03-16
sudo apt-get install xlibs-dev libxinerama-dev libxxf86vm-dev libxxf86misc-dev libxxf86dga-dev

should sort you for most situations.

---

### Post by obelix on 2005-03-16
[QUOTE=daniels]sudo apt-get install xlibs-dev libxinerama-dev libxxf86vm-dev libxxf86misc-dev libxxf86dga-dev

should sort you for most situations.[/QUOTE]
 What is your apt sources list? Apt can't get any of the packages except the first one.

---

### Post by obelix on 2005-03-16
Also I'm now having issues with the following while building another package:

Error: The following dependencies failed to build: jpeg libpng zlib tiff

What package is required to build these dependencies?

---

### Post by daniels on 2005-03-16
Sorry, I just guessed at using Hoary -- I'm too used to that now.  If you're on Warty, just install xlibs-dev and xlibs-static-dev.  For the rest, install libjpeg-dev, libpng-dev, libtiff-dev and zlib1g-dev.

---

