---
title: "libneon27-gnutls &quot;NEON API NOT STABLE&quot;"
date: 2008-09-06
forum: Installation &amp; Upgrades
---

### Post by HobbitTR on 2008-09-06
I use Ubuntu 8.04 (Hardy) on a Dell 1520 and have had very few problems with installation or updating. Today I had several security updates and two of them are subversion and libsvn1, however they require libneon27-gnutls. 

There is a warning message on libneon27-gnutls "neon is an HTTP and WebDAV client library, with a C language API. WARNING: THE NEON API IS NOT YET STABLE."

I have searched for information and have found several bug reports at packages.ubuntu.com and launchpad.net and a few others but none of them gave me an indication if this is safe to install.

---

### Post by HobbitTR on 2008-09-06
I was able to find a local answer to my question:

It's just a warning for developers. It means that the function names
etc... might change without any other warning. If you are not developing
an application that uses that library, and you trust your distro, then
it won't be any trouble for you.

---

