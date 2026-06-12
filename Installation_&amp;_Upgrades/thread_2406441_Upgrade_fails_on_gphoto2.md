---
title: "Upgrade fails on gphoto2"
date: 2018-11-21
forum: Installation &amp; Upgrades
---

### Post by gert5 on 2018-11-21
Hi All,

On a Linux machine running 'Ubuntu 14.04.5 LTS' that I haven't used a while I have the gphoto2 tool ([http://gphoto.org/](http://gphoto.org/))
The tool tells me this is its current version:
```

$ gphoto2 -v
gphoto2 2.5.3

Copyright (c) 2000-2014 Lutz Mueller and others

gphoto2 comes with NO WARRANTY, to the extent permitted by law. You may
redistribute copies of gphoto2 under the terms of the GNU General Public
License. For more information about these matters, see the files named COPYING.

This version of gphoto2 is using the following software versions and options:
gphoto2         2.5.3          gcc, popt(m), exif, cdk, aa, jpeg, readline
libgphoto2      2.5.3.1        all camlibs, gcc, ltdl, EXIF
libgphoto2_port 0.10.0         gcc, ltdl, no USB, serial without locking
```

Checking the tool's home page. [URL="http://gphoto.org/"]http://gphoto.org 
[/URL]
It says that the current version is : libgphoto2 and gphoto2 2.5.20

I tried > sudo apt-get dist-upgrade -f and it did tons of wonderful things.

But still the version of gphoto2 is 2.5.3. (not 2.5.20)

What's the trick?

Thanks,
Gert

---

