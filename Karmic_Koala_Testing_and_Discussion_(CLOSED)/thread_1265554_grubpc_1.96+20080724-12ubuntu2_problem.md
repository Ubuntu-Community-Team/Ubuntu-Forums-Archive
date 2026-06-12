---
title: "grubpc 1.96+20080724-12ubuntu2 problem"
date: 2009-09-13
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by flavouride on 2009-09-13
encountered an old problem this morning supposingly  solved ages ago:

Have been using grub2 for a few months now and never encountered such problem before.

after a few updates 2 days ago and having not shut down my jaunty amd64 for 2 days, when I rebooted this morning, grub 2 said: "unknown command 'initrd'" after the countdown.

I Ctrl+Alt+Del to the menu again and the same problem occured

then I used "e" to check and both the linux and initrd lines were correct; but same problem occured when I Ctrl+X to boot

finally booted into jaunty64 livecd, and chroot and install-grub /dev/sda; then rebooted and noticed the problem was solved

But 'til now I still don't know what was the cause of the problem.

how does the mbr bit of grub2 work? Would and how would grub2 in mbr corrupt itself?

Any suggestions?

---

### Post by hiaslboy on 2009-09-22
> **flavouride said:**
> encountered an old problem this morning supposingly  solved ages ago:

Have been using grub2 for a few months now and never encountered such problem before.

after a few updates 2 days ago and having not shut down my jaunty amd64 for 2 days, when I rebooted this morning, grub 2 said: "unknown command 'initrd'" after the countdown.

I Ctrl+Alt+Del to the menu again and the same problem occured

then I used "e" to check and both the linux and initrd lines were correct; but same problem occured when I Ctrl+X to boot



The package is broken and is missing initrd.mod

Ciao, Matthias

---

