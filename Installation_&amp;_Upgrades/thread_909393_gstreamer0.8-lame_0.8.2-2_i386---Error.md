---
title: "gstreamer0.8-lame_0.8.2-2_i386---Error"
date: 2008-09-03
forum: Installation &amp; Upgrades
---

### Post by Antihero20 on 2008-09-03
When trying to install this: **gstreamer0.8-lame_0.8.2-2_i386** so i can rip CD's to mp3's i get this error 

"**Error: Dependency is not satisfiable: libgstreamer0.8-0**"

The description of the error is:
"GStreamer plug-in encoding mp3 songs using lame.
Plug-in for encoding mp3 with lame under GStreamer.
This package is in PLF as it violates some patents.
(Based on a conversion of the gstreamer0.8-lame-0.8.2-1plf.i586.rpm package by alien version 8.44.) "

I've been unsuccesful in finding a solution for this

---

### Post by sayakb on 2008-09-03
As it says, install **libgstreamer0.8-0 **first and then install the package. Install any other such dependencies it prompts as needed for installing the package.

EDIT: Oh btw, gstreamer 0.8 is not the latest version in the repos. If you have the latest packages installed, you should have libgstreamer 0.10 installed. Download the 0.10 version of the package from [http://packages.ubuntu.com](http://packages.ubuntu.com) and install the newer one instead of this one.

---

### Post by Antihero20 on 2008-09-03
Ok so it turns out i do have the newer version but still does that mean there is a newer version of the gstreamer lame???

Cause still no success

---

