---
title: "[SOLVED] Default boot OS"
date: 2008-09-22
forum: Installation &amp; Upgrades
---

### Post by davdun on 2008-09-22
I have WinXp installed (first) and have successfully installed Ubuntu in dual-boot config. I am new to Linux tho and use XP mostly. How can I set up so WinXP is the default boot OS (not Ubuntu) without having to wait for the menu to make the OS selection? When I work on XP and have to reboot, I must always wait for this screen, or if I miss it, wait for Ubuntu to load then reboot (time issue, especially with automatic reboots in XP for various tasks).
:confused:

---

### Post by uberdonkey5 on 2008-09-22
there is a file called menu.lst  (that is an L not a number 1).
this holds all the boot up info for grub.

in the terminal (applications/accesories) type:

> sudo gedit /boot/grub/menu.lst

to allow you to edit the file (sudo means superuser, so you'll need to give your password after this, gedit is an editing program)

All the lines marked with '#' are comment lines but several lines down there should be a line which says:

default 0

zero is the first item in your boot in list (usually ubuntu). If windows XP is the 3rd item in your list, just change it (for example) to

default 2

Usually there are recovery mode boot in choices as well. Just select the standard XP bootin. Another item whilst you are there is the timeout. This is the time it takes to make a choice. This should be a few lines below default. Usually it is 10 seconds, but if you want it to boot quicker try something like 2 seconds i.e. change to:

timeout 2

(one second is sometimes too quick. With the time out, as soon as you select an arrow key the computer will wait for you, so you have 2 secs to press an arrow key, then as much time as you need to change the bootup choice). Basically, this will stop the long wait that happens when it is waiting for you to choose.

Don't forget to select 'save' from the menu, then reboot to try it out :)

---

### Post by davdun on 2008-09-23
Done and done. Thanks for the walkthrough.

---

