---
title: "Error executing &quot;grub-install (hd0)&quot; failed. - Fatal Error"
date: 2008-09-13
forum: Installation &amp; Upgrades
---

### Post by satya10123 on 2008-09-13
Hi,
I have a intel-centrino duo machine with 120 GB SATA disk. Win Vista is installed on the primary partition of the hard disk (recognized as sda by Ubuntu LiveCD) and Ive selected 1 partition(sda6) as "/" during installation.

The installation (Hardy Heron) progresses fine till 94% (after detection of hardware etc) and fails with the error message :

[B]Error executing "grub-install (hd0)" failed.
Fatal Error
[/B]
Of course, on reboot I don't get any grub and get straight booted into the Vista partition.

Btw I have lenovo laptop with "one touch recovery" i.e. At the time of startup&#8230; there is a button called lenovo care in notebook which intrupts normal windows boot and lead to recovery module&#8230; using this module I can reinstall vista as it was at the time of factory production.

Firstly, is there anything wrong in my selected configuration. If not, any tips on how I can resolve this problem / move ahead ?

Thanks in advance.

---

### Post by caljohnsmith on 2008-09-13
See [post #6 from this thread]("http://ubuntuforums.org/showthread.php?t=810205&highlight=circumvented+ext2+ext3") and I think it will solve your problem. Let me know how it goes, or if you still have the same problem after trying the method from that thread.

---

