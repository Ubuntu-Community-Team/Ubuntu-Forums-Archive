---
title: "U14 LTS install on Dell t7810 stuck at initial startup"
date: 2015-03-18
forum: Installation &amp; Upgrades
---

### Post by bryan46 on 2015-03-18
I ordered this Inspiron T7810 from Dell

Specs

(2) 6 core intel Xeon
32GB RAM
500 GB HD 

It was initially installed with 12.04LTS, but I attempted to upgrade and it kept failing.  So I burned a disk of Ubuntu Server 14.04.2.  Booted to the external CD-ROM, 1 partition, LVM, install went fine, no errors.

It said to reboot, but on the initial reboot it appears to be stuck at this message:

"adding33472508k swap on /dev/mapper/Olympus--vg-swap_1. Priority: -1 extents:1 across:33472508k FS"

It's been there for about 30 minutes now. The Hard drive activity light is flickering, but nothing else is happening.

Any idea what is going on? Is there an additional debug level to show me what is going on that I can enable?

---

### Post by bryan46 on 2015-03-18
According to this site:  [http://www.ubuntu.com/certification/hardware/201405-15065/](http://www.ubuntu.com/certification/hardware/201405-15065/)

this platform is certified to run 12.04. Does that mean that 14.04 is different enough to not support this platform, or does that mean that if 12.04 supports it, that it should be supported on 14.04 as well?

---

### Post by QIII on 2015-03-18
Hello!

Did you verify the md5sum on the image you downloaded?

---

### Post by bryan46 on 2015-03-18
they match... it's a good download

---

### Post by bryan46 on 2015-03-18
so update:

3rd time installing (U14, dell Recovery U12, U14), then freshly installed system is stuck at "systemd-udevd[386]: starting version 204"

I think I'm going to install another OS... don't have time for this shite... I did when I was dealing with Windows 2000, but I need an OS that 'Just Works'.

I'll run a quick OpenBSD install, and put dmesg here...

---

