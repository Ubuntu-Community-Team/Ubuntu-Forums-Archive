---
title: "Cannot uncompress Kernel 2.6.27"
date: 2008-11-05
forum: Installation &amp; Upgrades
---

### Post by jsemczyk on 2008-11-05
Hi,

After an upgrade from Hardy to Interpid, my new kernel cannot load.

Grub is working, I still have the kernel from Hardy (2.6.22) and it loads correctly.

The new kernel says : "Input has invalid flags" and stops, I don't even see the "uncompressing kernel" message.
After a little diging into google and my kernel sources I found out that this message comes from a gunzip function. Sounds like the kernel cannot uncompress itself.

I compared an md5sum of the vmlinuz file from an other computer that can load it and it is the same:
c81662bda04c60af62e822498394ee7e  /boot/vmlinuz-2.6.27-7-generic

CPU is : Intel(R) Core(TM)2 CPU          6300  @ 1.86GHz
I have 4 GB of RAM

Anyone have any hints ? I dont know where to go next.

---

### Post by jsemczyk on 2009-04-09
Answering to myself.

It was a Grub issue, after upgrading Grub it did not upgrade the files in /boot/grub/

I copied those found in /usr/lib/grub/ into /boot/grub/ and it worked.

---

### Post by fazza on 2009-04-09
hehe thanks for posting the answer :)
sorry none of us helped... though i have to say I wouldn't have known anyway :\

---

