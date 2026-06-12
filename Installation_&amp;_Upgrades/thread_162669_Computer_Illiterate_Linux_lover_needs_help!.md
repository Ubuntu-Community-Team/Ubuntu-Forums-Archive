---
title: "Computer Illiterate Linux lover needs help!"
date: 2006-04-19
forum: Installation &amp; Upgrades
---

### Post by BeckyTJ on 2006-04-19
Hello everyone,

I am certainly embarrassed to ask for your help, but I know very little baout computers but would love to ditch the microsoft giant - and to do that I need your help!

I just tried several times to boot ubuntu on to my new Compaq Presario v5000.  To do that, I changed the boot order to boot from the CD, and then I just hit enter when it asked me if I wanted to do anything expert.  It started to decompress the files, but then just blanks out and never installs anything.  The last thing I see is something to the effect of "trying to install the frame buffer"  (it goes by really fast).  What am I missing?

Thanks so much.

---

### Post by cgjones on 2006-04-19
When you boot the CD, look for something about boot options. It should be one of the F keys (F1, F2, etc). There is information in there on how to disable the framebuffer. Instead of pressing Enter to boot, you would type something like this then press Enter.
```
linux debian-installer/framebuffer=false
```
I'm not sure if this is the exact line or not, so look at some of the options and try it out. Hope this helps.

This link has more detailed information on the boot options.
[http://archive.ubuntulinux.org/ubuntu/dists/warty/main/installer-i386/current/doc/manual/en/ch05s02.html](http://archive.ubuntulinux.org/ubuntu/dists/warty/main/installer-i386/current/doc/manual/en/ch05s02.html)

---

### Post by aysiu on 2006-04-19
Could be a bad disk image...
[http://www.linuxiso.org/viewdoc.php/verifyiso.html](http://www.linuxiso.org/viewdoc.php/verifyiso.html)

---

### Post by Sgood1971 on 2006-04-19
try...

```
linux vga=771
```

at the boot prompt

---

