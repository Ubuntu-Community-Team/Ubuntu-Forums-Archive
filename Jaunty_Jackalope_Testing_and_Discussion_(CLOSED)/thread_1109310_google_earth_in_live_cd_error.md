---
title: "google earth in live cd error?"
date: 2009-03-28
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by sdowney717 on 2009-03-28
> ./googleearth-bin: relocation error: /usr/lib/i686/cmov/libssl.so.0.9.8: symbol BIO_test_flags, version OPENSSL_0.9.8 not defined in file libcrypto.so.0.9.8 with link time reference


was testing it out before an upgrade from interpid
any thoughts?
I simple downloaded the .bin file

---

### Post by ubulette on 2009-03-29
You are supposed to install googleearth-package from multiverse and run make-googleearth-package, then install the resulting deb.

See [http://ubuntuforums.org/showthread.php?t=1109767](http://ubuntuforums.org/showthread.php?t=1109767)

This is the recommended way to do it as it adds the needed dependencies for you and it will also makes upgrades easy.

You can also just do:

```

sudo mv /usr/lib/googleearth/libcrypto.so.0.9.8 /usr/lib/googleearth/libcrypto.so.0.9.8.moved_away

```

..and track the missing deps yourself :(

---

