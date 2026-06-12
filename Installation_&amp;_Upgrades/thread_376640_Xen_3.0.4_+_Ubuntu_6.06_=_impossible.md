---
title: "Xen 3.0.4 + Ubuntu 6.06 = impossible?"
date: 2007-03-05
forum: Installation &amp; Upgrades
---

### Post by pfastre on 2007-03-05
Hello

I'm trying to install Xen 3.0.4 on a new server on Ubuntu 6.06.
I chose 6.06 because of the long term support.

The setup is working, but I have a severe problem with TLS (thread local storage).
The xen documentation says to disable TLS: mv /lib/tls /lib/tls_disabled. It's bad for performance they say.
But I get the following problem:
[http://lists.xensource.com/archives/.../msg00685.html](http://lists.xensource.com/archives/.../msg00685.html)

So enabling TLS means a slow Xen performance. Disabling means a non-working Xen (because it needs TLS).
This problem is new in xen 3.0.4: [http://lists.xensource.com/archives/.../msg00608.html](http://lists.xensource.com/archives/.../msg00608.html). 

The conclusion is: either recompile your own version of glibc ([http://wiki.xensource.com/xenwiki/XenSpecificGlibc](http://wiki.xensource.com/xenwiki/XenSpecificGlibc)) or move to ubuntu 6.10 edgy. Or maybe someone created a package with an updated glibc?
What's best: recompiling glibc or moving from 6.06 to 6.10? This is a production server, which will be used for several years, hopefully without reinstalling it.

Thanks in advance for your reply.

---

