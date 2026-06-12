---
title: "error 22 after partition copy"
date: 2007-04-27
forum: Installation &amp; Upgrades
---

### Post by slambrick on 2007-04-27
I decided to resize my partition to allow a bit more space for Feisty Fawn. All seemed well. used Gparted to copy partition to new space made. then cleaned old space and expanded partition.
Completely broekn on reboot. Grub Stage 1.5 Error 22
Can anyone help me fix this please? O am running this from the live cd for Feisty.
Cheers:shock: :redface:

---

### Post by ajgreeny on 2007-04-27
Try reinstalling grub using the live CD like this:-
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

I suspect you have ended up in this situation as a result of a change in the partition name on which ubuntu is now installed, but it could be other things gone wrong.  Whatever it is, if there is a ubuntu installation on your machine then this ought to do the trick.
God luck!

---

