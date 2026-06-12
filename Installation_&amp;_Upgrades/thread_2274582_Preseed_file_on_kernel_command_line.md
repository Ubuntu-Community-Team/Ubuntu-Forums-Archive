---
title: "Preseed file on kernel command line?"
date: 2015-04-20
forum: Installation &amp; Upgrades
---

### Post by W_Sanders on 2015-04-20
I am trying to load a preseed file as a kernel argument. I forget where I saw this used as an example, but my pxelinux.cfg entry looks like this:

```
       kernel /images/ubuntu-14.04.2-server-x86_64/linux
        ipappend 2
        append initrd=/images/ubuntu-14.04.2-server-x86_64/initrd.gz ksdevice=bootif lang=  vga=784 text  auto-install/enable=true hostname=wmsboot domain=foo.bar suite=trusty preseed/file=/preseed/wmsboot.preseed debian-installer/locale=en_US kbd-chooser/method=us preseed/interactive=true
```

The parameter seems to be ignored, when it boots I see "successfully loaded preseed file from file:///preseed.cfg".

Is this supported? Seems not.

---

