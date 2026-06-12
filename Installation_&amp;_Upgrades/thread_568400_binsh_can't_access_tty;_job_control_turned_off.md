---
title: "/bin/sh: can't access tty; job control turned off"
date: 2007-10-05
forum: Installation &amp; Upgrades
---

### Post by xarket on 2007-10-05
I know there are other threads relating to this but they all have something with computers that already have a working distro of linux on them.

This is a fresh, brand new laptop from cyberpowerpc, and I have just installed vista on it, nothing else.  There is one partition with Vista, another data partition, made by the Vista start up, and then about 40g unpartitioned atm.

/bin/sh: can't access tty; job control turned off

That's what I get when I try to install, right after I hit start or install ubuntu, it brings a loading screen for a while and then a prompt.

here is my pc [http://www.cyberpowerpc.com/system/Xplorer_X5-7900_Notebook/](http://www.cyberpowerpc.com/system/Xplorer_X5-7900_Notebook/)

help! I really want to try ubuntu! That's the main reason I bought this laptop.

---

### Post by Pumalite on 2007-10-05
Try Alternate CD. Or see if you can boot Live CD with this:

At the LiveCD initial boot screen:
Select F6 for more options
Add the following option to the beginning of the options list:
break=top
Press enter to start booting
Ubuntu will start booting, but kick you out to a command prompt; at the prompt type these two commands:
modprobe piix
exit

---

### Post by xarket on 2007-10-05
when I do this I lose the screen, I think the laptop monitor is pretty sensitive about screen size, is there any way I can force the monitor to 1200x800 besides through the f4 thing at the bottom during the install prompt?

---

### Post by Pumalite on 2007-10-05
[http://ubuntuforums.org/showthread.php?t=258484&highlight=kernel+booting+parameters](http://ubuntuforums.org/showthread.php?t=258484&highlight=kernel+booting+parameters)

---

