---
title: "Install Ubuntu 14.04 alongside Debian Wheezy"
date: 2015-04-23
forum: Installation &amp; Upgrades
---

### Post by vvanherk on 2015-04-23
Hello.


First off, I'm a bit of a Linux novice, thus the question.


I have a laptop primarily used for a client work.  It is running Debian Wheezy, and wish to keep it intact in case I need to do more work for client.


I would like to install Ubuntu 14.04 alongside Debian, and use Ubuntu as a bit of a play/experiment area, etc.  HD has lots of space (600GB free), and as far as I can tell Grub is installed in MBR.


I did some searches, and from what I can tell, it sounds like I can just install Ubuntu from ISO file, specify how much space to use (say 400GB), and that's it.    This sounds almost too easy.   Once I install and restart machine, will there be selection for what Distro to boot.


Any input and advice appreciated.

---

### Post by Bucky Ball on 2015-04-23
Welcome. It should be that easy, theoretically(!), but I prefer to choose 'Something Else' at the partitioning section and manually set the partitions. Probably safer that way. You can choose not to install grub, or install it to the partition you are installing Ubuntu to (/), reboot the machine after install (it should still boot to Debian), boot Debian if you need to, open a terminal and 'sudo update-grub'. That should add Ubuntu to the selections next time you boot the machine.

If you choose 'Something Else' you also have the option to use the existing /swap and /home (if you have one). Just set /swap and /home to 'Use partition' but NOT ticked to format. Ubuntu will know what you mean and consider the existing /swap and /home the place to go (without wiping existing data on the /home partition, but ALWAYS backup before doing what you're doing).

You download the ISO file but then you need to burn the image to installation media, either disk or USB, boot and install from that.

---

### Post by vvanherk on 2015-04-23
Thanks Bucky Ball.   I'll be giving that a whirl over the weekend.  Cheers

---

