---
title: "Cannot find Kernel Sources for Gusty"
date: 2007-11-07
forum: Installation &amp; Upgrades
---

### Post by ZeroYuy on 2007-11-07
So, I'm TRYING to install ndis wrapper. Using Synpatic works okay, but there errors in ndiswrapper itself, and I feel that in the newest Ndis stable release, there might be fixes to these errors. However, whenever I try, I get this:

```

justin@justin-desktop:~/Desktop/ndiswrapper/ndiswrapper-1.49$ make
make -C driver
make[1]: Entering directory `/home/justin/Desktop/ndiswrapper/ndiswrapper-1.49/driver'
Makefile:35: *** Cannot find kernel version in /lib/modules/2.6.20-16-generic/build, is it configured?.  Stop.
make[1]: Leaving directory `/home/justin/Desktop/ndiswrapper/ndiswrapper-1.49/driver'
make: *** [all] Error 2

```

So, I looked around, and I got that I have to run sudo apt-get install linux-headers-$(uname -r) to get the headers

```

justin@justin-desktop:/lib/modules$ sudo apt-get install linux-headers-$(uname -r)
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package linux-headers-2.6.20-16-generic is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package linux-headers-2.6.20-16-generic has no installation candidate

```

So anyone have any ideas? I'm pretty new, so is there some magic I'm missing? I just upgraded to Gusty the other day. Incase it's needed...

```

Linux justin-desktop 2.6.20-16-generic #2 SMP Sun Sep 23 19:50:39 UTC 2007 i686 GNU/Linux

```

---

### Post by Pumalite on 2007-11-07
The kernel you are showing is not Gutsy. If you are running Feisty, I think you are out of luck. The headers are not available in the repositories (I think).

---

### Post by ZeroYuy on 2007-11-07
> **Pumalite said:**
> The kernel you are showing is not Gutsy. If you are running Feisty, I think you are out of luck. The headers are not available in the repositories (I think).


Then perhaps I need more help, because going into "About Ubuntu" on the "System" tab shows me this 

"Our first release (Warty Warthog) was in October 2004 so its version was 4.10. This version (Gutsy Gibbon) was released in October 2007 so its version number is 7.10."

Under the area that says "Version and Release Numbers". Is it a typo or was there an error during the upgrade? Or am I just being very noobish and missing some apparent?

---

### Post by ZeroYuy on 2007-11-07
> **ZeroYuy said:**
> Then perhaps I need more help, because going into "About Ubuntu" on the "System" tab shows me this 

"Our first release (Warty Warthog) was in October 2004 so its version was 4.10. This version (Gutsy Gibbon) was released in October 2007 so its version number is 7.10."

Under the area that says "Version and Release Numbers". Is it a typo or was there an error during the upgrade? Or am I just being very noobish and missing some apparent?

I just noticed that on my GRUB, it's not Ubuntu 7.10, kernel 2.6.20-14, it's Ubuntu 7.10, kernel 2.6.22-14. I imagine THIS is my problem (Being in Ubuntu 7.10, kernel 2.6.20-16 boot option).

However, I cannot boot into the Ubuntu 7.10, kernel 2.6.22-14 GRUB listing. It freezes at "Finding files needed to boot...". Should I start a new thread, or is there somewhere that addresses this?

---

### Post by Pumalite on 2007-11-07
Then you need:

sudo apt-get install linux-headers-`uname -r`

---

