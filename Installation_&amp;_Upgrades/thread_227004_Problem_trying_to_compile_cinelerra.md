---
title: "Problem trying to compile cinelerra"
date: 2006-08-01
forum: Installation &amp; Upgrades
---

### Post by hkl8324 on 2006-08-01
I followed this guide
[http://www.ubuntuforums.org/showthread.php?t=188264&highlight=cinelerra](http://www.ubuntuforums.org/showthread.php?t=188264&highlight=cinelerra)

and when I type ./configure
It showed a line:

  FreeType 2              missing

How can I fix this? (I thave freetype2 already installed, and it seems that there is no dev pachage on the official repo...)
(And I have litttf-dev already installed)

Thanks in advance

---

### Post by croak77 on 2006-08-01
You have libfreetype6-dev installed?

---

### Post by hkl8324 on 2006-08-01
Oh...I installed libfreetype6-dev and it works...
Thanks

---

### Post by hkl8324 on 2006-08-01
...But I have another problem now...:D

eo.o .libs/output.o .libs/reconstruct.o .libs/seek.o .libs/slice.o .libs/vlc.o .libs/mmxidct.o .libs/reconmmx.o
ar: .libs/reconmmx.o: No such file or directory
make[3]: *** [libmpeg3_video.la] Error 1
make[3]: Leaving directory `/opt/hvirtual/libmpeg3/video'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/opt/hvirtual/libmpeg3'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/opt/hvirtual'
make: *** [all] Error 2

What is it about?

---

### Post by croak77 on 2006-08-01
> **hkl8324 said:**
> ...But I have another problem now...:D

eo.o .libs/output.o .libs/reconstruct.o .libs/seek.o .libs/slice.o .libs/vlc.o .libs/mmxidct.o .libs/reconmmx.o
ar: .libs/reconmmx.o: No such file or directory
make[3]: *** [libmpeg3_video.la] Error 1
make[3]: Leaving directory `/opt/hvirtual/libmpeg3/video'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/opt/hvirtual/libmpeg3'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/opt/hvirtual'
make: *** [all] Error 2

What is it about?

[http://www.ubuntuforums.org/showthread.php?t=188264&page=3](http://www.ubuntuforums.org/showthread.php?t=188264&page=3)

---

