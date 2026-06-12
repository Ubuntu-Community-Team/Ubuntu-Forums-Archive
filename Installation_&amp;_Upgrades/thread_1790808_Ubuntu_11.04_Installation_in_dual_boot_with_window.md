---
title: "Ubuntu 11.04 Installation in dual boot with windows 7"
date: 2011-06-25
forum: Installation &amp; Upgrades
---

### Post by ahmed_ on 2011-06-25
Hello,

I am trying to install ubuntu 11.04 on my dell laptop (N5010).
I have the following partitions:

1) OEM (39 MB)
2) System (100 MB)
3) C (windows intallation) (100 GB)
4) D (150 GB)
5) E (~220 GB)

I shrank my C drive 10 GBs to make space for ubuntu but during installation of ubuntu it shows only the first 3 partitions (OEM, system, C (reduced)) and all the rest as one chunk of unusable hard disk space).
In windows I can see this chunk as three distinct partitions.
Please Help.

---

### Post by oldfred on 2011-06-27
Welcome to the forums.

Did you create these partitions in Windows? Windows does not use the standard extended partition for extra partition but converts to a proprietary LVM - logical volume manager.

[http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk.html](http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk.html)
Dynamic volume is a Microsoft proprietary format developed together with Veritas (now acquired by Symantec) for logical volumes.

Post a screen shot from windows to see if partitions are still basic or converted to dynamic. Per windows it is a one way conversion and the only way to unconvert is to back up entire drive and repartition. Some third party tools may do it without losing data, but I would still have backups if you want to try that.

---

