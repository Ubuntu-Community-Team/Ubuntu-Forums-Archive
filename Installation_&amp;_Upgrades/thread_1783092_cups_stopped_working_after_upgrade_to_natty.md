---
title: "cups stopped working after upgrade to natty"
date: 2011-06-15
forum: Installation &amp; Upgrades
---

### Post by banifou on 2011-06-15
I've an Epson_Stylus_SX525WD printer which was working fine till I upgraded to natty. 
Now cups stops the print jobs. I found following in the error logs: 
> Epson_Stylus_SX525WD: error while loading shared libraries: libpng12.so.0: failed to map segment from shared object: Permission deniedThat's odd because the library is there:
> lrwxrwxrwx  1 root root        18 2007-12-05 18:04 libpng12.so -> libpng12.so.0.23.0
lrwxrwxrwx  1 root root        18 2007-12-05 18:04 libpng12.so.0 -> libpng12.so.0.23.0
-rwxr-xr-x  1 root root    542163 2007-12-05 18:04 libpng12.so.0.23.0
lrwxrwxrwx  1 root root        10 2007-12-05 18:04 libpng.a -> libpng12.a
lrwxrwxrwx  1 root root        11 2007-12-05 18:04 libpng.la -> libpng12.la
lrwxrwxrwx  1 root root        11 2007-12-05 18:04 libpng.so -> libpng12.so
lrwxrwxrwx  1 root root        16 2007-12-05 18:04 libpng.so.3 -> libpng.so.3.23.0
-rwxr-xr-x  1 root root    555291 2007-12-05 18:04 libpng.so.3.23.0
I tried reinstalling the driver (epson-inkjet-printer-workforce-635-nx625-series_1.0.1-1lsb3.2_amd64.deb), nothing helps.

Thanks in advance for your help.

---

