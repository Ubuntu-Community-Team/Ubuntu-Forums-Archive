---
title: "GRUB Help"
date: 2006-04-13
forum: Installation &amp; Upgrades
---

### Post by shmuel on 2006-04-13
Hi

I am about to install fresh copies of XP and Ubuntu onto my computer. When installing Ubuntu is there anyway to disable GRUB from the beginning, when it gives the option, and still access Windows, as I want to install GRUB on the Windows partition. Does the install make Ubuntu the default OS?

Thanks for your help

---

### Post by oscar on 2006-04-13
Whenever I do a reinstall I install windows xp first onto a partition of the right size and then install ubuntu on the rest of the disk. The ubuntu installer should automatically detect that you have a windows xp install and add it to the grub menu. When you restart you should be able to select which OS you want to boot into. It is easy to change which one is default and adjust the timeout when booted into ubuntu in  /boot/grub/menu.list (the grub configuration file). Grub itself is installed into the disks Master Boot Record (the beginning of the disk) and controls how the operating systems are booted.

---

### Post by syg00 on 2006-04-13
[QUOTE=shmuel]... as I want to install GRUB on the Windows partition.[/QUOTE]You _really_ do ***_NOT_*** want to do this.

I mean *really*, *really*.
Overwriting the boot sector record of a Windows partition is a recipe for a total re-install.
See oscar's post above for the best option.

---

### Post by shmuel on 2006-04-13
OK

Thanks for your help...

I did think that what I was going to do was a bit complicated...

Thanks again

---

