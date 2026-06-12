---
title: "Can't Run 7.04 Installation Disk"
date: 2007-05-29
forum: Installation &amp; Upgrades
---

### Post by init1 on 2007-05-29
When I boot the ubuntu 7.04 installation disk, it gives me "Error reading boot disk" if I select "Start or Install Ubuntu". This is true on a CD or with qemu

---

### Post by scrooge_74 on 2007-05-29
your disk could have errors, which keep it from booting, try to burn another one at the lowest speed possible

---

### Post by init1 on 2007-05-29
The same thing happens if I run the iso in qemu

---

### Post by jerrylamos on 2007-05-29
How did the md5sum's compare.  I don't know which .iso you have, so for example:

md5sum feisty-desktop-i386.iso > feistymd5
takes a few seconds
then do cat fesitymd5
and compare to the md5sum from wherever you got the .iso from.  It must match exactly.  If not, then get it again.

Cheers, Jerry

---

### Post by init1 on 2007-05-29
Thanks, I forgot about the md5sum check. In fact, the md5sums do not match. Maybe another download will help

---

### Post by init1 on 2007-05-31
In fact, another download worked. Thanks!

---

### Post by lcjones on 2008-03-26
i'm having the same problem.  I'm very new to linux and any kind of CLI so could you tell me how to run the md5sum check.  I downloaded the iso file:  ubuntu-7.10-desktop-amd64.iso . I have an amd 64 bit processor.  Another question (although a bit off topic from this thread).  Is there anything different about the 64 bit version or is it just changed to utilize my processor better? Could I install the regular 32 bit version of ubuntu or would it not work?

---

