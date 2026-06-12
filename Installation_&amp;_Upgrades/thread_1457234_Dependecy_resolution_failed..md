---
title: "Dependecy resolution failed."
date: 2010-04-18
forum: Installation &amp; Upgrades
---

### Post by v923z on 2010-04-18
Hi All,

I had to update libc6 to version 2.11 on a 64-bit Karmic Koala, but since that version did not seem to be in the repositories, I managed the update by hand. Now, that produced some broken dependencies, as shown here 
```

v923z@penguin:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
  libc-dev-bin: Depends: libc6 (< 2.11) but 2.11.1-0ubuntu5 is installed
  libc6-dev: Depends: libc6 (= 2.10.1-0ubuntu16) but 2.11.1-0ubuntu5 is installed
  libc6-i386: Depends: libc6 (= 2.10.1-0ubuntu16) but 2.11.1-0ubuntu5 is installed
  libglib2.0-0: Depends: libc6 (< 2.11) but 2.11.1-0ubuntu5 is installed
  mountall: PreDepends: libc6 (< 2.11) but 2.11.1-0ubuntu5 is installed
  upstart: PreDepends: libc6 (< 2.11) but 2.11.1-0ubuntu5 is installed
  ureadahead: Depends: libc6 (< 2.11) but 2.11.1-0ubuntu5 is installed
E: Unmet dependencies. Try using -f.

```Is there a way to fix this? I mean, beyond using apt-get install -f? That will remove almost everything. However, this window that pops up every five minutes, informing me that there dependency resolution failed is getting a bit annoying. How can I disable that?
Thanks,
v923z

---

