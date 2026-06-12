---
title: "[SOLVED] 7.04 -&amp;gt; 7.10 via Update Manager: &amp;quot;Error during update&amp;quot;"
date: 2007-10-19
forum: Installation &amp; Upgrades
---

### Post by MegaJim on 2007-10-19
"A problem occurred during the update. This is usually some sort of network problem, please check your network connection and retry.

Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/feisty/free/binary-i386/Packages.gz](http://medibuntu.sos-sts.com/repo/dists/feisty/free/binary-i386/Packages.gz) 302 Found
Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/binary-i386/Packages.gz](http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/binary-i386/Packages.gz) 302 Found
Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/feisty/free/source/Sources.gz](http://medibuntu.sos-sts.com/repo/dists/feisty/free/source/Sources.gz) 302 Found
Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/source/Sources.gz](http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/source/Sources.gz) 302 Found"

Upgrading via the Upgrade Manager bombs out with this error every time I run it.

HTTP error 302: "302 Found

The requested resource resides temporarily under a different URI. Since the redirection might be altered on occasion, the client SHOULD continue to use the Request-URI for future requests. This response is only cacheable if indicated by a Cache-Control or Expires header field. "

So, if the resource resides temporarily under a different URI, shouldn't this be transmitted back to the update manager so it can find a package list elsewhere?  If anybody knows of an alternative repository or a way to get around this, I would be greatful

Regards,

James

---

