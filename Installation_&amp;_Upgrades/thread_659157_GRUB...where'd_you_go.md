---
title: "GRUB...where'd you go?"
date: 2008-01-05
forum: Installation &amp; Upgrades
---

### Post by G.TheDuke on 2008-01-05
I just re-installed Windows XP (I wish I could live without it) and to my dismay it's removed the GURB multiboot. Now, because I can't access the other drives in XP how do I get my mulit-loader back? Do I have to re-install Ubuntu too?

---

### Post by PmDematagoda on 2008-01-05
Use [SuperGRUB]("http://supergrub.forjamari.linex.org/?section=download") to restore GRUB back to the MBR, you can then make the proper configurations to run Windows XP as well.

---

### Post by ajgreeny on 2008-01-05
Or just use the ubuntu liveCD
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

