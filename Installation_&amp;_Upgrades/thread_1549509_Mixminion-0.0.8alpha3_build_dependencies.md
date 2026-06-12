---
title: "Mixminion-0.0.8alpha3 build dependencies?"
date: 2010-08-09
forum: Installation &amp; Upgrades
---

### Post by coljohnhannibalsmith on 2010-08-09
Hello,

After installing Tork, I attempted to install "Mixminion." Tork downloaded the source, but could not compile it.  While trying to compile it myself, I received the following message during the "make" stage:

/usr/bin/ld: ./contrib/openssl/libssl.a(s23_meth.o): relocation R_X86_64_32 against `.data' can not be used when making a shared object; recompile with -fPIC
./contrib/openssl/libssl.a: could not read symbols: Bad value
collect2: ld returned 1 exit status
error: command 'gcc' failed with exit status 1
make: *** [do_build] Error 1

Can anyone tell me what this means?  Does this mean I don't have the build dependencies satisfied?  Do I need to use a patch, or do I need to:

"recompile with -fPIC"

If so, how do I do this?

Any help appreciated.


Thanks, Hannibal

---

