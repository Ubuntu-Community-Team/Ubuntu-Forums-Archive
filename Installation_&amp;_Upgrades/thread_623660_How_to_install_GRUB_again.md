---
title: "How to install GRUB again?"
date: 2007-11-26
forum: Installation &amp; Upgrades
---

### Post by themad on 2007-11-26
Hello.
I've installed Window$ Vi$ta and now my GRUB isn't loading. I know that there was the same post but now I can't find it. Could someone help me with it?

To moderators: I'm sorry that I'm writting a post that there was before.

---

### Post by Herman on 2007-11-26
Hello themad, 
You can re-install GRUB with your Ubuntu 'Desktop' Live/Install CD. Just boot the CD, and open a terminal, and type 'sudo grub', and follow the instructions in post #2 of this thread, [HOW-TO install boot loader from Ubuntu]("http://ubuntuforums.org/showthread.php?t=609548")

An easier way would be to use [Super Grub Disk]("http://sgd.howto-linux.de/")


Regards, Herman :)

---

### Post by themad on 2007-11-26
Ok, so I did how it was written in [http://ubuntuforums.org/showthread.php?t=609548](http://ubuntuforums.org/showthread.php?t=609548) but when the computer starts, the GRUB screen flashes, and than Vista is loading automaticly. I've tried to pres the down cursor rapidly, but it doesn't works.

---

### Post by Herman on 2007-11-26
Hello themad,
If your 'grub screen flashes', I'm guessing that maybe GRUB has been installed with the IPL to your MBR okay, but possibly your /boot/grub/menu.lst file is configured to boot Windows by default and the timer is set to 1 or 0.

Here is a how-to that will explain to you the steps necessary to mount your Ubuntu file system from the Ubuntu 'Desktop' Live/Install CD, and access certain vital files in Ubuntu for inspection and for rescue purposes.
[                                  Mount a Ubuntu ext3 or reiserfs filesystem]("http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD") 
If you can follow the advice in the link given above, please check that your /media/ubuntu/boot/grub/menu.lst file is correctly configured and if not then you can edit it or post it here for help with editing it.
Or just post a copy of it here anyway and I'll check it for you, two sets of eyes are better than one.

Regards, Herman :)[COLOR=#666666][/COLOR]

---

