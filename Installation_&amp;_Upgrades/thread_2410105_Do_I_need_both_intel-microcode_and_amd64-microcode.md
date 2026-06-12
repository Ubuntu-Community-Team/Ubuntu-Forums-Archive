---
title: "Do I need both intel-microcode and amd64-microcode"
date: 2019-01-11
forum: Installation &amp; Upgrades
---

### Post by sunbear-c22 on 2019-01-11
For my systems with Intel CPU, I noticed that Ubuntu 16.04 and 18.04 distros will install the packages `intel-microcode` and `amd64-microcode`. What is the benefit of having both these packages installed? Should I remove the `amd64-microcode` given that I am not using an AMD CPU but an INTEL CPU? 

```

$ uname -rsvp
Linux 4.10.0-42-generic #46~16.04.1-Ubuntu SMP Mon Dec 4 15:57:59 UTC 2017 x86_64

```

---

### Post by deadflowr on 2019-01-11
It doesn't matter, removing one will just reinstall it later.
They're dependencies of kernel updates.

It won't be of any added benefit, but also it doesn't hurt either.
It's inaffective and the space it eats is negligible (around less than 2 megabytes)

---

### Post by Impavidus on 2019-01-11
I don't know the specifics of these packages, but normally AMD64 refers to the AMD64 architecture, which is the 64 bit architecture invented by AMD but used by both AMD and Intel CPUs.

---

### Post by deadflowr on 2019-01-11
In most cases we refer to amd64 as the arch=type (64-bit), but in this particular case it actually does refer to cpu brand.

Also more on why it's now a default depends of the linux-meta packages (meta packages being linux-generic and the linux-image-generic/latency packages):
[https://bugs.launchpad.net/ubuntu/+source/linux-meta/+bug/1738259]("https://bugs.launchpad.net/ubuntu/+source/linux-meta/+bug/1738259")
And that has to do with Meltdown/Spectre:
[https://wiki.ubuntu.com/SecurityTeam/KnowledgeBase/SpectreAndMeltdown]("https://wiki.ubuntu.com/SecurityTeam/KnowledgeBase/SpectreAndMeltdown")

---

### Post by sunbear-c22 on 2019-01-14
Thank you @deadflower and @Impavidus.

---

### Post by dondymenelo on 2019-01-16
I Agree! if you're using AMD architecture you should always go what's compatible on it otherwise there will be a problem. Not sure though what those updates do.

---

