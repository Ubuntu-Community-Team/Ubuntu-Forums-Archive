---
title: "Dual boot ubuntu and vista[Ubuntu installed first]"
date: 2008-05-22
forum: Installation &amp; Upgrades
---

### Post by cooldudeny on 2008-05-22
Hi so currently i have ubuntu installed on my laptop but now i will like to have vista on my laptop too and i know i can make it dual boot but what i am trying to understand is how can i install vista on top of ubuntu so that i can have a dual boot?

can someone please help me with this

---

### Post by sandysandy on 2008-05-22
have a look here

[http://ubuntuforums.org/showthread.php?t=207870](http://ubuntuforums.org/showthread.php?t=207870)

[http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm](http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm)

[http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm](http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm)

regards

---

### Post by Ichido on 2008-05-22
> **cooldudeny said:**
> Hi so currently i have ubuntu installed on my laptop but now i will like to have vista on my laptop too and i know i can make it dual boot but what i am trying to understand is how can i install vista on top of ubuntu so that i can have a dual boot?

can someone please help me with this

Install Vista FIRST, use Entire Hard Drive.
Boot from Ubuntu Live CD.
Partition Hard Drive, don't forget a "Linux-Swap" Partition (1GB to 2G?).
Install Ubuntu on New Partition, (10GB Minimum?) and RE-Write MBR.
GRUB will then List Ubuntu First & Windows Second.

---

### Post by eyeonthewinner on 2008-05-22
1) If you don't have your disk(s) partitioned, use gpardit to resize the ubuntu partition.
2) Install vista on the free space
3) Get the supergrub boot disk [here]("http://supergrub.forjamari.linex.org/") and boot to that disk. Use that to fix the grub.

Thats it!! good luck, post back if you need anything else

> **Ichido said:**
> Install Vista FIRST, use Entire Hard Drive.
Boot from Ubuntu Live CD.
Partition Hard Drive, don't forget a "Linux-Swap" Partition (1GB to 2G?).
Install Ubuntu on New Partition, (10GB Minimum?) and RE-Write MBR.
GRUB will then List Ubuntu First & Windows Second.

that will delete all your data from the ubuntu install, my way wont..

---

