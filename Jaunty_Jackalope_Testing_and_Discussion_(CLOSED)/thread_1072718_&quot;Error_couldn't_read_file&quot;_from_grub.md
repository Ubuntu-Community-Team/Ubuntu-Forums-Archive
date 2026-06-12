---
title: "&quot;Error: couldn't read file&quot; from grub"
date: 2009-02-17
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by prog99 on 2009-02-17
Hi there.

Just started getting this when selecting to boot from grub. Was fine until a few hours ago when I did a apt-get upgrade.

Testing system - 

64bit intrepid upgraded to jaunty with ext4. Kernel 2.6.28-7

Funnily enough if I choose an older intrepid kernel it'll boot but obviously dies when mounting the file systems as I guess they are not ext4 aware.

Booted up with an ext4 aware rescue cd and the disks check out fine and all the kernel files its looking for are there. I did a reinstall of the kernel but with no luck.

Any clues?

Thanks, Mike.

---

### Post by prog99 on 2009-02-20
Solved by a boot into the rescue disk and then uninstalling grub2 and putting grub back on

---

