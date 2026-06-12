---
title: "Stuck at BusyBox v1.1.3 when trying to load Ubuntu v7.10 i386"
date: 2008-04-12
forum: Installation &amp; Upgrades
---

### Post by missbliss on 2008-04-12
i am booting ubuntu 7.10 i386 from a mounted e:// drive mounted by magicdisk

the dual boot screen comes up with option to boot windows xp or ubuntu.

when i choose ubuntu, the ubuntu boot screen comes up and the bar goes back and for for a minute or two and then i get this:

Busybox v1.1.3 (Debian 1:1.1.3-5 ubuntu 7) Built-in Shell (ash)
Enter 'help' for a list of built in commands
(initramfs)


when i type in help there is a list of commands that i have no clue what to do with.  as far as i know the installation is complete and went well.


any help?

---

### Post by warp99 on 2008-04-13
You may have a corrupt initrid.img especially if you updated that file recently. Try this:

Boot up the computer and at the 'Grub loading' prompt press escape. When the first kernel line is highlighted press 'e', scroll down to highlight the initrid=/boot/initrd.img line press 'e' again. At the end of the string append a '.bak' without the quotation marks, then press 'b' to boot. If there's a backup file you'll be able to boot to the previous version.

If this doesn't work you can rebuild the initrid.img with a Ubuntu install disk, but first try this.

---

### Post by missbliss on 2008-04-13
i guess, i should have mentioned:  i don't have an older version. 

i'm an ubuntu/linux newb.

---

### Post by warp99 on 2008-04-13
Well we can go in and rebuild the file, it's not that difficult, but first I need to know the partition device your drive is using as root, where you installed Ubuntu. Is it /dev/sda1? or /dev/sda2? or /dev/hda1? or /dev/hda2? and so on. I need this so I can type you a list of commands to use in order to rebuild the file.

---

