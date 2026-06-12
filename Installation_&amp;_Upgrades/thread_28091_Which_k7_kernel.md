---
title: "Which k7 kernel?"
date: 2005-04-18
forum: Installation &amp; Upgrades
---

### Post by bailout on 2005-04-18
Just done clean kubuntu install and I now want to upgrade the kernel to a k7 version for AthlonXP and then install nvidia drivers. I see there are entries for k7 kernels in both "main" and "main-restricted". What, if anything, is the difference? Also there are several "kernel-k7" packages but I am not sure which one I need. I found this thread on the question but I am still unsure [http://www.ubuntuforums.org/showthread.php?t=27694](http://www.ubuntuforums.org/showthread.php?t=27694) If I want to install nvidia-glx afterwards do I install just linux-k7 or do I need to install linux-restricted-modules-k7 as well?

---

### Post by Leif on 2005-04-22
linux-k7 depends on  linux-restricted-modules-k7 so it will be installed anyway. just go ahead and install linux-k7, works fine for me.

---

### Post by NaplesBill on 2005-04-22
Just a little FYI, I tried the K7 kernel with my Sampron 2200+ and the 686 kernel is faster!

---

### Post by bailout on 2005-04-25
Interesting that you think the 686 is faster. I posted a thread asking k7 or 686 for AthlonXP/Sempron and didn't get a definitive answer [http://www.ubuntuforums.org/showthread.php?t=22218&page=1&pp=10](http://www.ubuntuforums.org/showthread.php?t=22218&page=1&pp=10) It is annoying that such a fundamental question is causing so much confusion with no official response.

How did you judge it to be faster? ie was it just your general impression or did you benchmark in any way?

---

### Post by NaplesBill on 2005-04-25
Well, the biggest difference is that screen drawing and refreshes are much snappier using the i686 kernel.  With the K7 kernel some animations(cursor, menus, etc...) seem to drag and cause trails similar to the trailing cursor option used on older lcds.

I don't know what it is about my system that causes this but using the i686 kernel seems to resolve it.

---

### Post by Turin Turambar on 2005-04-25
I'm running K7 kernel on my Athlon 2600+ and it works just fine!

---

