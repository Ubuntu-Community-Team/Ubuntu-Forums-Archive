---
title: "tired of  Apache2 Start Fail: undefined symbol"
date: 2013-11-10
forum: Installation &amp; Upgrades
---

### Post by pgm416 on 2013-11-10
I searched again for "apache2 fail: undefind symbol" and found no good recent posts.  I had this problem when I first installed the apache2 server and found out that is was the libapr libs. A "strings" on the usr/lib/apr* found the symbol. The newer versions in /usr/local/apr/lib did not have it.  The .so was linked to the usr/lib version, but the /usr/local/lib/*.so.0 was not. I relinked the /usr/local/apr/*.lib.so.0 to the /usr/lib/libapr* versions and it fixed apache2 so it would start.  It was running just fine for a long time, then a connect to my svn server failed.  I found the same problem and fixed it. I do not know, but it was probably some upgrade which did it.

Enjoy!

---

