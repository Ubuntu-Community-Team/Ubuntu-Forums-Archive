---
title: "Strange Error when trying to install from Add/Remove in Hardy"
date: 2008-05-13
forum: Installation &amp; Upgrades
---

### Post by J.Byram on 2008-05-13
So,

I get this strange error when trying to install any program from the Add/Remove tool in Hardy Heron.  This is the error:

[INDENT]W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/universe/libs/libsidplay/libsidplay1_1.36.59-4_i386.deb](http://archive.ubuntu.com/ubuntu/pool/universe/libs/libsidplay/libsidplay1_1.36.59-4_i386.deb)
  Size mismatch


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/universe/g/gst-plugins-ugly0.10/gstreamer0.10-plugins-ugly_0.10.7-3_i386.deb](http://archive.ubuntu.com/ubuntu/pool/universe/g/gst-plugins-ugly0.10/gstreamer0.10-plugins-ugly_0.10.7-3_i386.deb)
  Size mismatch[/INDENT]

I got this error because I was trying to play a DVD and it said that I did not have the appropriate codecs.  It then recommended for me to download the GStreamer Extra Plugin package and then it gave me that error.

Any suggestions?
Could this be an effect of my upgrade from Gutsy to Hardy yesterday?

Thanks
-John

---

### Post by kellemes on 2008-05-13
Could you try the following from terminal please?
```
sudo apt-get update
```

Now try to install again..

---

### Post by J.Byram on 2008-05-13
> **kellemes said:**
> Could you try the following from terminal please?
```
sudo apt-get update
```

Now try to install again..
Thanks, that worked awesome!

---

