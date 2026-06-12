---
title: "Package is referred to by another package"
date: 2005-08-21
forum: Installation &amp; Upgrades
---

### Post by twelvegates on 2005-08-21
Hello,

I'm trying to install gkrellm:
```
apt-get install gkrellm
```
This tells me
```
Package gkrellm is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package gkrellm has no installation candidate
```
What does this mean?
How can I install gkrellm?

-Hanspeter

---

### Post by az on 2005-08-21
You need to enable the universe repository in synaptic, then do an update.

---

