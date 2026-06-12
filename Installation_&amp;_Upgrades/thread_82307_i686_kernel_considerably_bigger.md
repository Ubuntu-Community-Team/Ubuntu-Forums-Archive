---
title: "i686 kernel considerably bigger???"
date: 2005-10-26
forum: Installation &amp; Upgrades
---

### Post by RikoW on 2005-10-26
Hi everybody,

under Hoary, i had both the i386 and the i686 kernel installed on a 15MB boot partition (somehome kept this size for historical reasons:). I was still trying out the i686 that why I still had both.

Now, I did a dist-upgrade to Breezy and had considerable problems, because the kernel images would not fit on the boot partition, at least not both. Turns out, the i386 fits alone, with still about half the partition empty (including all the grub stuff).
But, even after removing i386 I cannot install i686 fully, because it fills up the whole partition. Is that easy to understand, why the i686 2.6.12 kernel is so much bigger than i386 or i686 for 2.6.10?

Currently, I don't have much time to play with that more, but I'd rather have the more fitting kernel running.

Thanks and Cheers,

                      Riko

---

### Post by RikoW on 2005-10-27
ok, never mind what I said before. 686 is slightly bigger but of course fits, when I remove 386 first .... brought my pulse up for a few minutes, though!

now, I'm happily running the 686 kernel.

Cheers,

            Riko

---

