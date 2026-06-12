---
title: "GTK orphan thinks linux-generic should be removed?"
date: 2010-05-27
forum: Installation &amp; Upgrades
---

### Post by tzjin anthony ks on 2010-05-27
hi all

i'd posted a gtk orphan thread earlier, which might have been a bit too broad, and i'm trying to rephrase my question to be a bit more narrow in its scope.

so, i fire up gtkorphan, open the options section, and check "show all orphan packages, not only those in the libs section". in the list of packages that this generates, i see "linux-generic" and "linux-image-2.6.32-21-generic" (screenshot is attached)

this brings me to a couple of (possibly silly) questions - (1) what will happen if i uninstall these two packages? (2) is there a way to prevent gtkorphan from reporting needed packages as orphaned? (3) does there exist a program that reports on how often an installed package has been run in the past week/month/etc?

thanks in advance.

tzjin.

---

### Post by dino99 on 2010-05-27
dont worry, follow my previous post, these packages have been updated so these ones can be removed, but check the 2 options and select all instead of none

---

### Post by tzjin anthony ks on 2010-05-27
dino,

are you seriously suggesting that i remove linux-image-2.6.32-21-generic ? it's one of the two kernels in my menu.lst file.

cheers.

tzjin.

---

### Post by dino99 on 2010-05-27
if you doubt deselect it :P

which release are you running ? which kernel is used ?

i repeat: i've never had issue with gtkorphan

---

### Post by tzjin anthony ks on 2010-05-27
i'm running lucid, 2.6.32-22, and keeping 2.6.32-21 (just in case).

i've had issues with gtkorphan before - it would uninstall something, and then my audio would not work, or flash support is gone, and things of that nature. i had to hibernate packages to ensure that my system works properly.

besides, my original questions were more fundamental than looking for a quick-fix: are these two packages really orphans? if not, why does gtkorphan report them as orphans?

cheers.

tzjin.

---

### Post by dino99 on 2010-05-27
[http://www.marzocca.net/linux/gtkorphan.html](http://www.marzocca.net/linux/gtkorphan.html)

---

### Post by tzjin anthony ks on 2010-05-27
excellent!

this builds up nicely to the next question - there are packages like linux-generic, and inkscape, that i know are top-level packages. and then there are others, such as libgtksourceview-common that i know i dont explicitly use, but may be needed for added functionality of other packages.

is there a way of finding out which packages have been run in the past month/week/etc?

cheers.

tzjin.

---

