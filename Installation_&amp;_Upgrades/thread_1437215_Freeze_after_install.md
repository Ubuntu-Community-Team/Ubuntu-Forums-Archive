---
title: "Freeze after install"
date: 2010-03-23
forum: Installation &amp; Upgrades
---

### Post by jmerkin on 2010-03-23
Hi all,

I've been through a number of installs before. I am now trying to install (k)ubuntu on a toshiba satellite L500. It will either stall before progressing to the installation  or when it reboots after finishing if I use the test installer. I tried 9.10 and 10.4beta and it's the same thing. It will either stall with a blank screen (but somewhat responsive: ctrl+alt+prtsc+R,E,I,U,B,S will reboot it), or a text listing similar to dmesg output:

```
[0.91034]  [<ffffffffff8124382>] (text)
``` repeated over and over where (text) is some stuff about acpi, kernel_init, schedule_tail, or child_rip. I'm really unsure of how to approach this.

It has the Intel HM55 wireless integrated chipset. Any ideas?

---

### Post by jmerkin on 2010-03-23
The google was a bit more helpful since my last attempt. It seems it is indeed a problem with the HM55 chipset. Apparently it is rather new and needs the most current kernel build. Pulled this from this posting

[http://ubuntuforums.org/showthread.php?t=1393413](http://ubuntuforums.org/showthread.php?t=1393413)

---

### Post by jmerkin on 2010-03-24
so, apparently 2.6.33 works for some people, but i am not included in that grouping. i upgraded to it and i get the same error. anybody have an idea?

edit: following the approach from the other posting, i added nomodeset to the grub command and then dropped to a root shell. if instead of going to the shell i resume normal boot and then start X, i get the blank screen.

---

