---
title: "Recover glibc/libc from failed update"
date: 2014-04-10
forum: Installation &amp; Upgrades
---

### Post by mms2 on 2014-04-10
Hi,

I needed to upgrade libc for an app I wanted to install, however this machine has no net connection, so I downloaded elsewhere and transferred there through an external hdd. (it's no problem doing that quickly if it's needed for the fix)

I got the source though (should probably have tried a .deb package?) and followed the instructions to config, build and install glibc. At the end of sudo make install, it complained of a segfault and now X is not starting and a few core utils too (like gawk and find!) but many stuff are still working and even the external hdd is automatically detected and i can mount and copy stuff over.

Researched the problem, it seems glibc requires all optional libs to be the same build, and since I only tried to upgrade the core, existing ones are not compatible (dmesg seems to complain mostly about libm)

I can also access the install CD (or boot into repair mode if necessary) and tried to copy and dpkg glibc over, which worked flawlessly, only it was not glibc but glib!:popcorn: And I dunno where glibc is on the CD...  but I'd hope I could upgrade directly to the new version by downloading that instead and dpkg it in place? Though getting it back to working condition would be nice if that is not possible. :-) but how?

thanks.

---

### Post by mms2 on 2014-04-11
Fixed by reinstalling... =/

Now how would I upgrade my libc6 with no net access? (I think I better create a new thread for that)

---

