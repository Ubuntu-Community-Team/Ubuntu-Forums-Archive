---
title: "Epson C110 - how to set up?"
date: 2008-02-18
forum: Installation &amp; Upgrades
---

### Post by b.m on 2008-02-18
Hello, all.

I have an Epson C110 that I need to have working with Ubuntu. As far as I found out, gutenprint  version 5.0.2 has added this printer to the pool of supported printers.

It is not very clear for me how the printing technology is setup in Ubuntu. Are we using cups? gutenprint? both? It's been a few years  since Ihad to touch printing in Linux (my previous printer was pretty standard), which makes me uncomfortable in changing these by instinct.

So, my question is:

1. Am I the only one with an Epson C110? If not, how did you solve it?

2. cupsys-driver-gutenprint 5.0.2 was added on hardy[1]. However, I am not willing to upgrade my system to the current alpha release. How can I make a partial upgrade on this other than manually downloading all the dependencies (and there are quite a few) ?

[1] [http://packages.ubuntu.com/hardy/graphics/cupsys-driver-gutenprint](http://packages.ubuntu.com/hardy/graphics/cupsys-driver-gutenprint)

Thanks!

---

### Post by b.m on 2008-02-19
It was solved as shown here:  [http://ubuntuforums.org/showthread.php?p=4361101](http://ubuntuforums.org/showthread.php?p=4361101)

I installed the new version of gutenprint (5.0.2) from hardy repositories, thus adding support for my printer. Thanks to sisco311 for pointing in the right direction [1]!!

[1] [http://ubuntuforums.org/showthread.php?p=4361101](http://ubuntuforums.org/showthread.php?p=4361101)

---

