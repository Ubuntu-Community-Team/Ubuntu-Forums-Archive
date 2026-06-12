---
title: "Before I Install Again"
date: 2007-06-13
forum: Installation &amp; Upgrades
---

### Post by lemonwonder on 2007-06-13
Hi.

Today I sucessfuly dual-booted with win98. I still got the linux partition, and am happy to install. Windows is alredy on there, not willing to un-install.


First of All:
~~~~~~~

I need a way to hide grub unless ESC or F1 or whateva key is pressed, this is essential. Or atleast to make windows 98 the default OS.

~~~~~~~~~~~~~~~~~~~~
I changed the setting to be able to login through admin account, then I couldnt login, it loaded up, a brown screen with a mouse loading button thing. How can I fix?

~~~~~~~~~~~~~~~~~~~~~~~~
Are there any cool effects, tricks or pieces of software I shoudl know of?

~~~~~~~~~~~~~~~~~~~~~~~~~~~~
Anything else I should know???




THANKS!

---

### Post by bernardfrancois on 2007-06-13
First of all: you would get more replies if you created seperate threads for each issue, and gave them subjects describing the actual issues.

Having said that...

1) To hide grub you need to make some changes in the grub configuration file, 'menu.lst' if I recall correctly. Searching this forum or your hard drive will tell you the location of the file.
If you put the line to boot windows first, grub will boot to windows by default.
It's also possible to change the amount of time grub appears and to put grub on a floppy disk (so the menu will never show up, unless you have the floppy disk inserted. More informatino can be found by searching the forum.

2) You should never login as root. If you want to start an application as root, you can open a terminal and type 'xhost +', then 'sudo su', and then the name of the executable of the application you want to start as root.

3) For more information you could check the beginners section of this forum, or search for tutorials, introductions etc

---

