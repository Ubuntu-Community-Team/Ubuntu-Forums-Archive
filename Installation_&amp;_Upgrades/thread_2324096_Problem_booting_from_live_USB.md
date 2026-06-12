---
title: "Problem booting from live USB"
date: 2016-05-10
forum: Installation &amp; Upgrades
---

### Post by ab6362 on 2016-05-10
i have a new lenovo p50, not booking from usb. I got this msg "missing parameter in configuration file. keyword: path gfxboot.c32: not a COM32R image". Typing help does not help.

---

### Post by oldos2er on 2016-05-10
Post moved to its own thread.

See [http://askubuntu.com/questions/486602/ubuntu-14-04-lts-live-usb-boot-error-gfxboot-c32not-a-valid-com32r-image](http://askubuntu.com/questions/486602/ubuntu-14-04-lts-live-usb-boot-error-gfxboot-c32not-a-valid-com32r-image) for potential solutions to this problem. Can you please tell us which version of Ubuntu you're trying to install?

---

### Post by sudodus on 2016-05-11
Welcome to the Ubuntu Forums :-)

It is a known bug. Please use another tool to create the USB boot drive. It works with a tool, that *clones* the iso file, for example [mkusb](https://help.ubuntu.com/community/mkusb) in linux or [Win32 Disk Imager](https://wiki.ubuntu.com/Win32DiskImager/iso2usb) in Windows.

---

### Post by ab6362 on 2016-05-11
thanks! I solved it the following way - I started ubuntu 16.04 from USB on my old laptop (lenovo T410), created another USB wiith 16.04 by using creator, and then started this USB on my new lenovo p50. Works as usual. thanks again for tips!

> **oldos2er said:**
> Post moved to its own thread.

Can you please tell us which version of Ubuntu you're trying to install?

ubuntu 16.04

---

### Post by sudodus on 2016-05-11
> **ab6362 said:**
> thanks! I solved it the following way - I started ubuntu 16.04 from USB on my old laptop (lenovo T410), created another USB wiith 16.04 by using creator, and then started this USB on my new lenovo p50. Works as usual. thanks again for tips!

Yes, the version of Startup Disk Creator in 16.04 uses the cloning method, which is very reliable. Thanks for sharing your solution :-)

Please click on **Thread Tools** at the top of the page and mark this thread as SOLVED

---

