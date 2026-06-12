---
title: "Ubuntu 7.10 dual boot vista (installed first)"
date: 2007-10-29
forum: Installation &amp; Upgrades
---

### Post by Galaxian on 2007-10-29
Hi

I have installed Ubuntu on a separate hard drive. I shrunk the existing partition to make room and installed on the 'unallocated space' using the manual method.

I made sure that 3 partitions were set up; two ext & swap. This included /boot so I thought Grub would not affect my Vista installation, however my MBR was trashed but I fixed that (got an error 22 when booting). I set all three as primary partitions although I am not sure if this was correct (I now have more than 4 primary partitions but Vista does not see the Ubuntu partitions except under the Computer Management console.

I thought that I could install Ubuntu completely separately and manage the dual boot in Vista by using EasyBCD 1.7. I' ve added a Linux entry and pointed to the /boot partition but am having no joy. I guess Grub needs setting up again but am reluctant to attempt from the LiveCD given my previous experience.

I have no Linux experience whatsoever but am willing to learn. Any pointers would be appreciated.

---

### Post by zvacet on 2007-10-29
[http://ubuntuforums.org/showthread.php?t=224351&highlight=grub]("http://ubuntuforums.org/showthread.php?t=224351&highlight=grub")

---

