---
title: "scim-python seg fault"
date: 2009-11-18
forum: Installation &amp; Upgrades
---

### Post by hlxshady on 2009-11-18
Hello all,

I have been using scim-python as my Chinese input method since 8.10.

And it has been working pretty well.

But after upgrading to 9.10, I now am not able to have it worked.

I have tried installation from the apt-get, or compile the source code. But either way results in a segmental fault when I try to start the
System -> Preference -> SCIM Input Method Setup.

Therefore I totally have no idea how to solve this problem.

Have anyone of you guys got an idea about that ?

Following is the output of dmesg after I tried to launch SCIM Input Method Setup:
[14739.853086] scim-helper-lau[11781]: segfault at 8 ip 00a68f63 sp bf91c480 error 4 in _scim.so[a5d000+1d000]



Thanks

---

