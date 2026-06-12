---
title: "LVPM on Ubuntu 9.10"
date: 2009-12-20
forum: Installation &amp; Upgrades
---

### Post by mr.moch on 2009-12-20
I'm trying to move my Wubi Ubuntu onto a dedicated partition via LVPM.  However, when I try to install LVPM, the following error occurs:

Error: Dependency is not satisfiable: grub

Any solution to this?

---

### Post by cavusmanus on 2009-12-26
karmic uses grub-common and grub-pc packages , which contain the needed files though.
so using 
dpkg -f depends -i <lvpm-package>
works if above packages are installed.
make sure to adjust grub.cfg (not meu.lst, another change) and run grub-install to boot from the right partition

---

### Post by bluefox815 on 2010-02-14
cavusmanus

I think the dpkg option you meant to use was --force and not -f, which stands for --field

the revised command would be:

dpkg --force depends -i <lvpm-package>


I ran into this minor mistake while trying to run LVPM for Ubuntu 9.10 myself :)

---

