---
title: "Unable to remove brother printer"
date: 2006-11-12
forum: Installation &amp; Upgrades
---

### Post by gmiles on 2006-11-12
Hi

I tried to install a brother hl1230 on my edgy, but now I get an error 

The package hl1230lpr needs to be reinstalled, but I can't find an archive for it.

I've tried sudo dpkg --force-remove-reinstreq -P hl1230lpr

But I get

dpkg - warning, overriding problem because --force enabled:
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
(Reading database ... 120345 files and directories currently installed.)
Removing hl1230lpr ...
/var/lib/dpkg/info/hl1230lpr.postrm: 3: /etc/init.d/lpd: not found
dpkg: error processing hl1230lpr (--purge):
 subprocess post-removal script returned error exit status 127
Errors were encountered while processing:
 hl1230lpr
Would be grateful for any ideas as I can't install any new packages till I get rid of this

Thanks Geoff

---

### Post by calvinpriest on 2006-11-13
Well, I just struggled with something similar myself, and here's what I had to do:
1) Go into /var/lib/dpkg/info and find the post-removal script (called something like "package.postrm").  Rename it.
2) apt-get remove package
3) dpkg --purge package

It's not pretty but it gets around the problem...

---

### Post by gmiles on 2006-11-15
Cheers That did the trick

Thanks again 

Geoff

---

