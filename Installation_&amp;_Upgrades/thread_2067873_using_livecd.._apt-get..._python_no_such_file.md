---
title: "using livecd.. apt-get... python: no such file"
date: 2012-10-07
forum: Installation &amp; Upgrades
---

### Post by ceagle on 2012-10-07
I'm using the livecd to attempt a rescue of an ubuntu server...

On this page... [https://help.ubuntu.com/community/LiveCdRecovery](https://help.ubuntu.com/community/LiveCdRecovery) under Update Failure

at apt-get update my system says "bash: /usr/bin/python: no such file or directory"

WAT?!?

---

### Post by mcduck on 2012-10-08
The instructions are a bit outdated, when the inbstructions tell you to do this:
```
sudo mount /dev/hda1 /mnt
```
...you should be doing this instead:
```
sudo mount /dev/sda1 /mnt
```
(And also keep in mind that you have to replace the sda1 with the correct name for your Ubuntu root partition...)

---

### Post by ceagle on 2012-10-08
hrmmm VERY strange.... I did mount the root partition... sda1.  The OS is there.... but no apt-get or python under /usr/bin.  apt-cache, apt-url are there.

I am 100% sure I did -not- remove those.

---

