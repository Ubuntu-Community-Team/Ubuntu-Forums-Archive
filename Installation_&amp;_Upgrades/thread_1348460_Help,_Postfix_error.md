---
title: "Help, Postfix error"
date: 2009-12-07
forum: Installation &amp; Upgrades
---

### Post by Mallam2001 on 2009-12-07
I started getting this error since an update and now cant install anything else without getting this fixed. Screenshot of error attached. Thank you

---

### Post by dstew on 2009-12-07
Some of these post-installation script problems are due to incomplete or broken packages. Usually, removing the package completely, then re-installing it will fix the problem. [Here]("http://www.khattam.info/2009/08/04/solved-subprocess-pre-removal-script-returned-error-exit-status-2-error/") is an article about one approach. I know the error returned is different, but the general process of removing and re-installing the offending package is the first thing to try.

If you get the error again, on the command line, copy all the relevant error message output and post it to the forum. There might be more clues in there as to what the problem is. I have seen some other posts that corrupted host names can trigger this problem.

---

### Post by Mallam2001 on 2009-12-08
Thanks for the link, it did help a lot and I managed to fix the problem from that and other posts .

---

