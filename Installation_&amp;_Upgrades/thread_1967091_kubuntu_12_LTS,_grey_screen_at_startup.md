---
title: "kubuntu 12 LTS, grey screen at startup"
date: 2012-04-27
forum: Installation &amp; Upgrades
---

### Post by MilouXXI on 2012-04-27
Hello,

I have just installed Kubuntu 12 LTS. After Grub boot  screen appears correctly the system does not start properly. It freezes  on an empty grey screen.

I tryed a system rescue with my install  dvd but it freezes too. Actually I had to choose nomodset when I  installed Kubuntu to boot the live cd otherwise it froze as well. But  using nomodeset i managed to use live CD to install without any issue. 

But  maybe there is a relation between the fact that i could not boot  normaly the live cd or use the live cd to make a system rescue and the  fact that now I cannot boot at all (after Grub pops up normally... so it  s not a boot loader issue). It looks like in both cases the system does  not want to load...

Any suggestions ?

Thanks!

---

### Post by MilouXXI on 2012-04-28
I just had to add nomodeset to the grub boot command

in grub press "e" to edit how to boot your system then add nomodeset after quiet splash.

to save changes edit grub file.

---

