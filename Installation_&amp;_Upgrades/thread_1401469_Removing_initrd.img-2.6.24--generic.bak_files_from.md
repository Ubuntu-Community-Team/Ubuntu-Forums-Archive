---
title: "Removing initrd.img-2.6.24-*-generic.bak files from /boot"
date: 2010-02-08
forum: Installation &amp; Upgrades
---

### Post by saitas on 2010-02-08
Dear all,

My attempt to update the Linux kernel image for version 2.6.24 on x86/x86_64 (linux-image-2.6.24-27-generic) failed due to a lack of disk space. I assume the "faulty" partition is the one hosting the /boot directory (/dev/sda2, with only 381 KB left out of a 116.2 MB total space). Before digging further, I would like to remove all the initrd.img-2.6.24-*-generic.bak files in it, totalling 45 MB. Is it safe?

Thank you in advance,

Mikhail

---

### Post by suseendran.rengabashyam on 2010-02-08
Hi,

I guess the old kernels in your Ubuntu machine needs to be uninstalled so that you can free up the /boot partition. You can follow this thread to remove the old kernels

[http://ubuntuforums.org/showthread.php?t=1283521](http://ubuntuforums.org/showthread.php?t=1283521)

Let me know if this helps.

---

### Post by saitas on 2010-02-09
Thank you, it did help indeed, so now I stand on safe ground again. It shows how robust Linux is, as I went quickly through lots of scary instructions which I half-understood and applied with my own ignorant way, and still worked!

Kind regards,

Mikhail

> **suseendran.rengabashyam said:**
> Hi,

I guess the old kernels in your Ubuntu machine needs to be uninstalled so that you can free up the /boot partition. You can follow this thread to remove the old kernels

[http://ubuntuforums.org/showthread.php?t=1283521](http://ubuntuforums.org/showthread.php?t=1283521)

Let me know if this helps.

---

### Post by F W Adams on 2010-04-30
Worked fine for me. I just followed post #8 in the link given. All the kernels you have installed are marked in green on the list. Just delete all except the one you are using.

---

