---
title: "Won't reboot after installation the HD"
date: 2007-05-29
forum: Installation &amp; Upgrades
---

### Post by Finishedwithwindows on 2007-05-29
After booting from an Desktop installtion CD and enjoying the experience, I decided to install to my hard drive.
Completed the entire process including partitioning a slave drive (my master drive has xp and no significant free space).
At the end of the installation rpocess, I get a prompt to remove the boot cd and close the drive. I do so and the system re-boots.
However, I do not get offered a chice of operationg systems, instead the only prompt I get is
Grub>

I can type help and get a list of commands but I was expecting either a choice of os or ubuntu to start.

I enjoyed running ubuntu from cd and would like to make this permanent.

Cheers

---

### Post by Heliix on 2007-05-29
Hello,
You may try to boot ubuntu directly by passing commands to grub. I had to do this once when I messed my system. There is an excellent description on [http://www.linuxselfhelp.com/gnu/grub/html_chapter/grub_4.html](http://www.linuxselfhelp.com/gnu/grub/html_chapter/grub_4.html)

Unfortunately, I have no experiences with slave disks, but I guess it will be recognized as /dev/hdb (and some number).
Once you manage to boot at least into console, you should then edit the /boot/grub/menu.lst (this configuration file for grub is really heavily commented and some examples are given as well)
Alternatively, you may boot from a live CD and check the /boot/grub/menu.lst file on your harddrive (and possibly edit it). 
I attached my menu.lst file (I have also a dualboot, ubuntu+XP)

Good luck and don't give up, linux is really worth it ;-)

---

### Post by Finishedwithwindows on 2007-05-31
Hello Heliix
I tried your suggestion, but to no avail.
I did get it working by making space on the master drive and partitioning that.
I now have a working dual boot machine, and I am still enjoying my learning curve with Linux.

Thanks for the help
:D

---

