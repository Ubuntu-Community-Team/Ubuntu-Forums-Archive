---
title: "Can I reformat a ext2 partition without killing MBR?"
date: 2007-10-22
forum: Installation &amp; Upgrades
---

### Post by sipickles on 2007-10-22
Hi,

I have plenty of windows (not vista) experience but am new to linux.

I installedhave Ubuntu feisty as a dual boot on my XP laptop. It wasn't used much since its a work machine and we use windows.

Now i've noticed that it won't boot Feisty. after selecting in grub, it goes to a black screen with a cursor flashing topleft (_ not a prompt).

I thought i'd try installing gutsy over the top but can't get that to work either! It prints 'Kernel Alive. Kernel direct mapping tables up to 100000000 @ 8000_d000' and freezes. Some forums suggest removing 'splash' and adding 'noapic nolapic nosplash' to the boot line but it makes no difference.

And they say ubuntu 'just works'! :)

Perhaps my two problems are connected. Can I reformat my linux partition and try a fresh install? or will it screw up my grub loader so I won't be able to boot windows (NOT an option if I value my job!)

Thanks for any advice.

AMD athon 64, nVidia 7300Go, 1MB ram

Simon

---

### Post by alastair on 2007-10-22
> **sipickles said:**
> 
Perhaps my two problems are connected. Can I reformat my linux partition and try a fresh install? or will it screw up my grub loader so I won't be able to boot windows (NOT an option if I value my job!)

Thanks for any advice.


A fresh install on top of the current linux partition will be fine.

The new install will recognise that one disk/partition is Windows, and let you choose to install Ubuntu on other partitions/disks. By default, it will also create a new boot record MBR for you - and include Windows and Ubuntu boot options.

It should just work. But as they say - if you cannot afford disaster, plan for it (backup).

Alastair

---

### Post by sipickles on 2007-10-23
Well, as an experiment I tried the Mandriva installer, and that had exactly the same problem.

It seems to hang just after the PCI output during text install


I've done my backup, so i'll try a reformat and clean install

---

