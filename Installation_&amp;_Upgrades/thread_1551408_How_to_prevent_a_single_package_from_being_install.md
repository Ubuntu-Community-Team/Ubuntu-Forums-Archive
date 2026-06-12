---
title: "How to prevent a single package from being installed as a recommended dependency?"
date: 2010-08-12
forum: Installation &amp; Upgrades
---

### Post by gzegzol on 2010-08-12
Hello,
I have a simple problem (at aptitude/apt/dpkg level).
I'm installing a package with lots of recommended dependencies. Let's say:
```
aptitude -y --with-recommends install ubuntu-desktop
```
I like the recommendations in general - but there is a single package (or a few of them), which I don't like to be installed.
Is there any reasonable way to express that?

Of course, one could get the list of packages to be installed --with-recommends, remove unwanted packages, and install --without-recommends.

The second obvious option is to remove unwanted packages after the installation.

Both presented solutions seem vulgar to me. I'm looking for a cleaner solution. Any ideas?

Blacklisting a package - preventing it from being installed by aptitude ever - is also fine with me. But I didn't find any way to achieve that.

---

