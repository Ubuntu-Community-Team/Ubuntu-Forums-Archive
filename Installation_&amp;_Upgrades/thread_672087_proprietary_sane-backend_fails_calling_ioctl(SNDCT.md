---
title: "proprietary sane-backend fails calling ioctl(SNDCTL_DSP_SYNC)"
date: 2008-01-19
forum: Installation &amp; Upgrades
---

### Post by md2k7 on 2008-01-19
Hello,

I'm fighting with my Samsung SCX-4521F printer/scanner to work under Ubuntu 7.10 Server (this means no GUI).
I've found quite a few tutorials on this device:

[http://hathawaymix.org/Weblog/2005-07-15](http://hathawaymix.org/Weblog/2005-07-15)
something similar: [https://lists.linux-foundation.org/pipermail/printing-user-samsung/2006/001335.html](https://lists.linux-foundation.org/pipermail/printing-user-samsung/2006/001335.html)
[http://www.elijahlofgren.com/ubuntu/#scx-4521f](http://www.elijahlofgren.com/ubuntu/#scx-4521f)
and probably some more that i don't remember now... even a German one...

... and I've managed to get printing to work. sane-find-scanner works well too, but scanimage -L doesnt find anything. Stacktracing it, I found:

stat64("/dev/usb/lp0", 0xbff8330c)      = -1 ENOENT (No such file or directory)
open("/dev/usblp0", O_RDWR)             = 3
ioctl(3, SNDCTL_DSP_SYNC, 0xbff82fc0)   = -1 EINVAL (Invalid argument)
close(3)                                = 0
stat64("/dev/usb/lp1", 0xbff8330c)      = -1 ENOENT (No such file or directory)
open("/dev/usblp1", O_RDWR)             = -1 ENOENT (No such file or directory)
stat64("/dev/usb/lp2", 0xbff8330c)      = -1 ENOENT (No such file or directory)

Looks like the (proprietary ](*,) ) SANE backend (libsane-smfp.so) finds the scanner, but then somehow tries to SYNC to it (with a system call for syncing to sound cards? :shock: ), which fails. On my other linux system (Suse 10.0), this call works fine (I got the scanner to work there approx. a year ago).

Then, ignoring the fact that it had found the device it was looking for, the backend continues looking on the other interfaces where the scanner is _not_ connected :( .

What should or can I do now? If the backend would have been open-source, I'd have digged into the source...

I'd really appreciate any help or hint,
Yours,
David Madl

---

