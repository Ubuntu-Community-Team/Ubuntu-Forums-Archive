---
title: "Read-only and Persistence on USB"
date: 2010-10-20
forum: Installation &amp; Upgrades
---

### Post by sdlynx on 2010-10-20
I recently put Linux Mint (child of Ubuntu) on a USB stick, and made it persistent.  However, as everyone knows, a persistent setup takes a much longer time to load and shut down than a non-persistent one.  So, I tried to edit my syslinux.cfg to make one option persistent and one not, like so:

```

...
label live
  menu label Start Linux Mint
  kernel /casper/vmlinuz
  append  file=/cdrom/preseed/mint.seed boot=casper initrd=/casper/initrd.gz quiet splash --
menu default
label persist
  menu label Start Linux Mint (p)
  kernel /casper/vmlinuz
  append  file=/cdrom/preseed/mint.seed boot=casper persistent initrd=/casper/initrd.gz quiet splash --
...

```

What I'd like is for the first entry to use the persistence file, but only as a read-only file.  Currently it just skips over the casper-rw altogether.

---

### Post by sdlynx on 2010-10-22
bump; help?

---

### Post by sdlynx on 2010-10-31
anybody?

---

