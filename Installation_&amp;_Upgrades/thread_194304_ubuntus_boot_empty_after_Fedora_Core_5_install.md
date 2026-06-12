---
title: "ubuntus /boot empty after Fedora Core 5 install"
date: 2006-06-11
forum: Installation &amp; Upgrades
---

### Post by johncarter on 2006-06-11
Hi

I had / have ubuntu installed on my athlon64 /dev/hdc3, all was ok.
i then installed fedora core in /dev/hdc2 on the same machine.
towards the end of the instalation grub was installed on the mbr.
but unlike ubuntu fedora only picked up itself and XP. when i went back to /boot on /dev/hdc3 (the ubuntu partition) it was empty. i believe thi is where the kernel and other stuff is stored. how can i get the contents of /boot back

thanks john

---

### Post by Kapre on 2006-06-11
[QUOTE=johncarter]Hi

I had / have ubuntu installed on my athlon64 /dev/hdc3, all was ok.
i then installed fedora core in /dev/hdc2 on the same machine.
towards the end of the instalation grub was installed on the mbr.
but unlike ubuntu fedora only picked up itself and XP. when i went back to /boot on /dev/hdc3 (the ubuntu partition) it was empty. i believe thi is where the kernel and other stuff is stored. how can i get the contents of /boot back

thanks john[/QUOTE]

John - might as well give [this]("http://www.ubuntuforums.org/showthread.php?t=193804&highlight=reinstall+grub") a try.

K

---

### Post by johncarter on 2006-06-13
[QUOTE=Kapre]John - might as well give [this]("http://www.ubuntuforums.org/showthread.php?t=193804&highlight=reinstall+grub") a try.

K[/QUOTE]
i tried that already, after further investigation it looks like [fedora core 5 formats the /boot partition]("http://forums.whirlpool.net.au/forum-replies.cfm?t=499422") so the link you referenced has nothing to work with, i think it just searchs for instalation then link to them rather that reinstalling the kernel and intird files.
i suppose my next question do i need to reinstall unbunto to get these back, and will thank screw up FC5

thanks for you help all the same , john

---

