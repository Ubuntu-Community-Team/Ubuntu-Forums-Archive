---
title: "Non-existent URL updating Hardy"
date: 2010-08-18
forum: Installation &amp; Upgrades
---

### Post by goldsby on 2010-08-18
Updating Hardy using Update Manager.
It complains it can't find certain deb files: with good reason, the whole directory level is missing on the archive.  For instance:

archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-image-2.6.24-28-generic_2.6.24-28.73_i386.deb

There is no directory /ubuntu/pool/main/l/linux on archive.ubuntu.com.

The ls-lR.gz file, however, claims that there is such a directory and that it contains the deb file I'm looking for.

Am I not seeing straight or is something really whacked on the archive?

Thanks for any enlightenment.

---

### Post by goldsby on 2010-08-18
OK, I'm not seeing straight.

The directory listing was alphabetized in a non-dictionary fashion, with longer names like linux-atm preceding linux (I'd never noticed that before).

I removed firefox (I'd installed a version in advance of the version supported by Hardy) and suddenly it could find the other 3 (non-firefox) modules it couldn't find before.

---

