---
title: "Unbutu 10.10 HP DL320 G3"
date: 2011-06-04
forum: Installation &amp; Upgrades
---

### Post by technical.support on 2011-06-04
[FONT=Verdana][SIZE=3]I am trying to install Ubuntu 10.10 on a HP DL 320 G3.  I have the 2 80 GBs drive installed configured as a RAID1 using Ubuntu’s software RAID support.  I am able to install 10.10 and the OS loads; however, I am getting the following error trice:[/SIZE][/FONT]
[FONT=Verdana][SIZE=3] [/SIZE][/FONT]
[FONT=Verdana][SIZE=3]        Modprob: FATAL: Could not load /lib/modules/2.6.35-22-generic-pae/modules.dep: No such file or directory (2x)[/SIZE][/FONT]
[FONT=Verdana][SIZE=3] [/SIZE][/FONT]
[FONT=Verdana][SIZE=3]I tried the following two items with no success:[/SIZE][/FONT]
[FONT=Verdana][SIZE=3] [/SIZE][/FONT]
[FONT=Verdana][SIZE=3]1. sudo depmod –a and rebooted the system[/SIZE][/FONT]
[FONT=Verdana][SIZE=3] [/SIZE][/FONT]
[FONT=Verdana][SIZE=3]2. [COLOR=black]Boot the machine, log in and run 'sudo /sbin/depmod -ae' in a terminal window. This will create the module dependency listings for the kernel you run and on next boot that message should be gone.[/COLOR]  [/SIZE][/FONT]
[FONT=Verdana][SIZE=3] [/SIZE][/FONT]
[FONT=Verdana]As this system is going to be placed in production I would like to fix this error.[/FONT]

---

