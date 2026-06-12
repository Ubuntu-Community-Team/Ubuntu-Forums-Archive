---
title: "bug when installing kernel / no disk space"
date: 2013-01-19
forum: Installation &amp; Upgrades
---

### Post by KisteBecks on 2013-01-19
hi,


just run into a kind of but while upgrading the kernel.

it failed the first time and rebooting didnt work anymore, something was missing right after i saw the grub screen.

turns out that /boot was full, but somehow apt changed grub.conf but failed because there was not enough space to actually copy the kernel files.

so why does apt change the config before the files are copied?

---

### Post by ibjsb4 on 2013-01-20
There are several ways to remove old kernels.

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=remove+old+kernels&as_qdr=all&sa=Google+Search&lang=en](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=remove+old+kernels&as_qdr=all&sa=Google+Search&lang=en)

Im kinda keen on this one.

[https://help.ubuntu.com/community/Lubuntu/Documentation/RemoveOldKernels](https://help.ubuntu.com/community/Lubuntu/Documentation/RemoveOldKernels)

If your not comfortable with the command line, there are GUI ways listed in the first link.

---

