---
title: "Trouble installing K7 kernel"
date: 2005-10-15
forum: Installation &amp; Upgrades
---

### Post by Pathogenix on 2005-10-15
Greetings,

not content with knackering a hard drive under mysterious circumstances, I've decided to upgrade my kernel to a K7 build as I run an Athlon.

I've installed all the packages but this one:
```
Setting up linux-image-2.6.12-9-k7 (2.6.12-9.23) ...
```
This message will sit forever and ever and ever on my terminal until I finally tire of its taunting presence and ctrl-c. The hard drive chugs repetetively all the while, which suggests that _something_ at least is happening, or trying to happen.

When I kill the process, I get the following message:

```

Failed to create initrd image.
dpkg: error processing linux-image-2.6.12-9-k7 (--configure):
 subprocess post-installation script returned error exit status 2

```

ls /boot shows that the process _does_ manage to create a file named initrd.img-2.6.12-9-k7.new

---

