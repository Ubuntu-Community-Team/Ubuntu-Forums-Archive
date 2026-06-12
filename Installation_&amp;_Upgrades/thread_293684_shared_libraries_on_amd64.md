---
title: "shared libraries on amd64"
date: 2006-11-05
forum: Installation &amp; Upgrades
---

### Post by alion on 2006-11-05
--------------------------------------------------------------------------------

It's a fact, that on certain architectures (AMD64 among them), shared libraries must be PIC enabled.

But when I'm trying to link a library I get the following message:

libc.o: relocation R_X86_64_32 against `a local symbol' can not be used when making a shared object; recompile with -fPIC libc.o: could not read symbols: Bad value

So I already recompiled a bunch of the libraries my app is dependent of.
But I did that using source checkout and ./configure && make.

Is there a good-looking way to compile the whole runtime (libc + libstdc++,etc) with fPIC flag on Ubuntu?

---

