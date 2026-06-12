---
title: "PPA for modern GCC?"
date: 2010-09-29
forum: Installation &amp; Upgrades
---

### Post by akuda on 2010-09-29
Hi,

I am a software developer, presently porting a game engine from Visual Studio to GCC. I'm working on LTS 10.04.

The project uses C++ lambdas, and I really would like to keep it this way. Therefore, I need GCC >= 4.5 to compile it.

I wouldn't like to reinstall entire OS, or to have to manually update this single program every time.

Is there an option to update it from 10.10 repositories, pointing out, that I need only this package (and it's dependencies)? Or is there any PPA that does the trick for me?

Generally, the entire packaging system of Ubuntu rocks, as long as I can find up-to-date PPAs of all packages I need to have in recent versions (like mono).

Regards,
akuda

---

### Post by directhex on 2010-09-29
Unsupported & unmaintained for various technical reasons, but try [https://launchpad.net/~ubuntu-toolchain/+archive/test](https://launchpad.net/~ubuntu-toolchain/+archive/test)

---

### Post by akuda on 2010-09-30
great, thanks

but it lacks of C++ support. I tried with gcc -x c++, and it says that it mises cc1plus. Any clues?

Regards,
akuda

---

### Post by akuda on 2010-09-30
right, it didn't install automatically, and was not listed, but is there. sorry for inconvenience.

---

