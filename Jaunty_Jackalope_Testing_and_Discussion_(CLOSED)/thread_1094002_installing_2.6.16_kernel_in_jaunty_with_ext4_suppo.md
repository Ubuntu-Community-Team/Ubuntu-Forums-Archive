---
title: "installing 2.6.16 kernel in jaunty with ext4 support?"
date: 2009-03-12
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by KhaaL on 2009-03-12
I was going to help with doing some bugtesting for [bug 12309]("http://bugzilla.kernel.org/show_bug.cgi?id=12309") and my next step would be installing the 2.6.16 kernel. Now since don't use my wifi, losing it dosen't provide much of a problem. the problem lies instead that last time I compiled a kernel was *ages* ago, so is it possible to install this kernel from a older repo/PPA? Also I recently went over to ext4 and I've grown rather attached/dependant on it, is there a module for older kernels that can be loaded and provide support for ext4?

---

### Post by Taiebot65 on 2009-03-12
I do not think older kernel support ext4 for me only since 2.6.28 ext4 is supported.

---

### Post by autocrosser on 2009-03-12
In a word---no.....2.6.16 is far too old for ext4--newer than 2.6.27 only....

---

### Post by Kow on 2009-03-12
I wouldn't trust ext4 on any kernel < 2.6.28.

---

### Post by KhaaL on 2009-03-12
Argh, too bad. well, i guess that means I'll have to reformat and reinstall. Is there a painless way to install the mentioned kernel in jaunty then, or is a recompile required?

---

### Post by jfernyhough on 2009-03-12
Closest to 2.6.16 I could find in the repos was 2.6.15 from Dapper...

[http://packages.ubuntu.com/dapper-updates/base/linux-image-2.6.15-53-686](http://packages.ubuntu.com/dapper-updates/base/linux-image-2.6.15-53-686)

You'll need to sort out any dependencies manually, though.

Hope this helps. :D

---

### Post by KhaaL on 2009-03-12
> **jfernyhough said:**
> Closest to 2.6.16 I could find in the repos was 2.6.15 from Dapper...

[http://packages.ubuntu.com/dapper-updates/base/linux-image-2.6.15-53-686](http://packages.ubuntu.com/dapper-updates/base/linux-image-2.6.15-53-686)

You'll need to sort out any dependencies manually, though.

Hope this helps. :D

Thank you my friend, will install it tomorrow along with a reformat back to ext3 (grunt!). One last thing, I tried to find kernel headers in order to get the auto kernel module config thing (DKMS?) working but couldn't find it... any leads?

---

