---
title: "libsane 1.0.18 and checkinstall"
date: 2006-07-13
forum: Installation &amp; Upgrades
---

### Post by yetanothersteve on 2006-07-13
I needed libsane 1.0.18 for a big fix specific to my scanner, an Acer / Benq 310u that only shows garbled scans with the 1.0.15 to 1.0.17 backends.

I downloaded the libsane source tar.gz and uncompressed it and ran 

```
./configure
make
sudo checkinstall
```

Pre-requisites were that I had to install libusb-dev for usb scanner support and of course build-essential and checkinstall.

libsane installed fine to /usr/lib/local and I set up symlinks from /usr/lib to the sane directory and files in /usr/lib/local.
XSane and scanner are now working well.

My question: was there a better way to get this package into my Dapper system?

Also, is checkinstall still considered a valid way to install software on Ubuntu when using source packages?

I realize that changing the configuration to install directly to /usr/lib would have eliminated the need for symlinks.

---

