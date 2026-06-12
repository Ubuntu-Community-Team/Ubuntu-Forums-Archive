---
title: "Kernel Install - Linux Headers dependency problems"
date: 2010-08-29
forum: Installation &amp; Upgrades
---

### Post by HiroP on 2010-08-29
Hi there,
I am attempting to install a new kernel on my Ubuntu 10.04 installation to fix a problem I'm having with running StarCraft 2 on Wine.

I downloaded the source from git and then compiled the kernel.

I then installed the linux-image .deb file using dpkg but when trying to install the second linux-headers .deb file I receive an error stating that there are dependency problems:

```
sudo dpkg -i linux-headers-2.6.xx-x-generic_2.6.xx-x.xx~lucid1_amd64.deb 
(Reading database ... 173415 files and directories currently installed.)
Preparing to replace linux-headers-2.6.xx-x-generic 2.6.xx-x.xx~lucid1 (using linux-headers-2.6.xx-x-generic_2.6.xx-x.xx~lucid1_amd64.deb) ...
Unpacking replacement linux-headers-2.6.xx-x-generic ...
[B]dpkg: dependency problems prevent configuration of linux-headers-2.6.xx-x-generic:
 linux-headers-2.6.xx-x-generic depends on linux-headers-2.6.xx-x; however:
  Package linux-headers-2.6.xx-x is not installed.[/B]
dpkg: error processing linux-headers-2.6.xx-x-generic (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-headers-2.6.xx-x-generic
```Could anyone give me an idea as to why I might be receiving this error? Thanks.

---

