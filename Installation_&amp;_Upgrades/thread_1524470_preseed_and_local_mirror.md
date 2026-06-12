---
title: "preseed and local mirror"
date: 2010-07-05
forum: Installation &amp; Upgrades
---

### Post by hcpr on 2010-07-05
Hi, I'm trying to set up a network installation with preseed. Everything works fine (or seems to) as long as I use mirrors on the Internet. However I need to use a local mirror for this. From what I've been able to find, the following should work in the preseed file:

```
d-i mirror/http/hostname string 192.168.2.3
d-i mirror/http/directory string /ubuntu
d-i mirror/suite string lucid

```And if I boot the installer without preseed, and enter the information at the mirror select screen, everything works as expected. However if booted via preseed, the installer still tries to connect to no.archive.ubuntu.com (which is the one that matches the country settings).

Any suggestions as to what I need to put in preseed.cfg to get the same results as when I enter the selection manually?

Thanks :-)

---

