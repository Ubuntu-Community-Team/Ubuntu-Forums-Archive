---
title: "Installing the pine e-mail client on AMD64"
date: 2006-09-12
forum: Installation &amp; Upgrades
---

### Post by fruityoaty on 2006-09-12
I'm not sure if this is helpful, but I couldn't find anything about installing PINE on AMD64 machines in these forums, and there doesn't seem to be a package for it.  

I was able to compile it from the source with this command:

sudo ./build SSLDIR=/etc/ssl SSLINCLUDE=/usr/include/openssl SSLLIB=/usr/lib/ssl lnp

That's all one line, and I'm using Ubuntu 6.0.6 on an AMD Opteron machine.

-fo

---

