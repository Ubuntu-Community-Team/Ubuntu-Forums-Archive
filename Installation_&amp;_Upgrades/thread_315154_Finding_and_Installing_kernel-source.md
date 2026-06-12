---
title: "Finding and Installing kernel-source"
date: 2006-12-08
forum: Installation &amp; Upgrades
---

### Post by SatNav on 2006-12-08
Hey all,

First off, im pretty much a complete Linux noob. I can find my way around xp/dos pretty well, shell commands i can kind of manage, and I can use a search engine, but thats about it.

Second I hope this is in the right forum, if not -sorry, please move it.

Onto my problem. Im trying to get wifi running on an acx111 chipset pci card.  I've found a long-winded but thorough tutorial here:
[http://www.houseofcraig.net/acx100_howto.php](http://www.houseofcraig.net/acx100_howto.php)

I'm doing ok until i get to the bit that says 'verify the presence of the correct version of the kernel source' and directs me to type:
ls /lib/modules/`uname -r`/build/include/linux/version.h

this gives me the response:
ls: /lib/modules/2.6.15-27-amd64-generic/build/include/linux/version.h: No such file or directory

ok, so off to the package manager, and search for 'kernel-source'. I have enabled all four components (main restricted universe multiverse) under every 'sources' repository I can see, but the closest thing I get in the results is 'Linux kernel source for version 2.4.27 with Debian patches'. I dont think it's right, but what the hey, i install it. try again: it's not right.

I've googled about, and I keep seeing mention of kernel.org, along with a warning not to download sources from there, because they probably won't work, so now I'm stumped. Is the source package I found the right one? If so, am I missing something? If not, where do I find the right one? Please Help!

Thanks in advance,
Mark

---

### Post by natalia on 2006-12-13
Hello, Mark,

I am no expert either, but I think you might look for "linux-headers". Take a look at posts #3 and #4 in this thread:

[http://ubuntuforums.org/showthread.php?t=302969&highlight=please+install+kernel+source](http://ubuntuforums.org/showthread.php?t=302969&highlight=please+install+kernel+source)

I hope this helps!

---

