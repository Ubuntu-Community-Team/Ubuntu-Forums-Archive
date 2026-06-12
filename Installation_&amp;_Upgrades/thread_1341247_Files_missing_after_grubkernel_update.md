---
title: "Files missing after grub/kernel update"
date: 2009-11-29
forum: Installation &amp; Upgrades
---

### Post by pdjsyc on 2009-11-29
Hi,      I have problem with regular update of Ubuntu 9.10. After some actualisation there is no Ubuntu in the Grub - only Memtest and Windows. After trying to boot manually from grub I receieve file missing error. I checked from Live CD that in /boot directory there is only memtest and grub - no vmlinuz and initrd. After some file copys from second computer with the same os there are still some file missing. I have tried also copying /lib/modules/2.6.31-14.generic as it is also missing but still get more and more file missing errors including some in /proc directory.  As I can imagine it is some problem after regular update of linux kernel from version 2.6.31.14 to 2.6.31.15 - or problem with grub update at the same time? Can I perform update from live cd?    Problem exists on two machines. One is some brand new laptop with sata disk working as IDE. Other machine is desktop with single sata disk working through raid chipset (asus a7n8x motherboard).   On laptop I have already reinstalled OS did manual update and unselected linux-* and grub-* packets. It is working without any problems. On desktop machine i am searching for solutions.     If i have to copy files from other machine which ones exept from /boot and /lib/modules? Is /proc directory always empty on the disc?

---

