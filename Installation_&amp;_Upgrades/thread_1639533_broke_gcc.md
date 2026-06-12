---
title: "broke gcc"
date: 2010-12-06
forum: Installation &amp; Upgrades
---

### Post by SoulSurvivor on 2010-12-06
Hi, I'm running Karmic Koala netbook remix edition.
I was playing around with gcc trying to get an old version running and understand the system a little more.  I thought I had to download and install an old version.  I didn't find the old version (4.0.1) so I did a manual install into my /usr/local dir and other related directories.  It was working fine until my system did an update.  Then gcc seemed to break. I got this error:

/usr/local/lib/libgcc_s.so.1: version `GCC_4.2.0' not found (required by /usr/lib/libstdc++.so.6)

I fixed this by backing up libgcc_s.so.1 and making it a symbolic link to the original one that was used with the gcc that came with the operating system (/lib/libgcc_s.so.1)

Now I can run my applications again but I haven't tested out too much so far.  I'd like to remove the gcc that I manually installed but I'm not sure how to do that and not sure if it will break.  I may have changed some environment variables that the newer version depended on... but I'm not sure.

Can anyone help me?

---

