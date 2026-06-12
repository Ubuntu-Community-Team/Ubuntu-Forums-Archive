---
title: "Re-install question"
date: 2008-01-25
forum: Installation &amp; Upgrades
---

### Post by cpohlad on 2008-01-25
I have a Dell laptop that is partitioned 50/50 into Ubuntu and Windows XP.  Last night I had to rebuild my WinXP partition and lost Grub.  I still have all of the data on my Ubuntu partition, but no way to get into it at this point.  Is there an easy way to fix this?

---

### Post by stevescripts on 2008-01-25
Take a look at the Super Grub Disk - [http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)

Take your time ....

Steve

---

### Post by ajgreeny on 2008-01-25
Or simply use the ubuntu live CD.
Boot into the ubuntu live CD
open a terminal and run :
    sudo grub
This gets you to a simple grub command line.
Then:
    find /boot/grub/stage1
This will tell you where your /boot/grub/stage1 is which is needed to boot ubuntu. Replace the question marks in the following command with the output of the this last command :
    root (hd?,?)
[like : root (hdo,1) ,probably]
then:
    setup (hd0)
This is where your windows partition and MBR normally is, but if you want grub on another disk, use hd1, etc as appropriate. It's much easier to use the windows MBR and then just change the default boot system later if others in the family demand windows boots by default.
Then:
    quit
Finally reboot, and hopefully you will now have a working grub bootloader.

Good luck.

---

