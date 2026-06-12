---
title: "Error 17?"
date: 2005-07-03
forum: Installation &amp; Upgrades
---

### Post by soul on 2005-07-03
I just tried installing Ubuntu on a partitioned section of my external harddrive. The installation seemed to be going smoothly and when it came to the end it asked me to remove the cd so it could reboot and finish the installation. As it rebooted I got an error that said:

> GRUB Loading stage1.5.


GRUB loading, please wait. . . 
Error 17
and all I'm left with is a flashing underscore :(

Can anyone help me out here? I can't even get XP to start.

---

### Post by WildTangent on 2005-07-03
well, i dont know what error 17 is, but i do know how to restore the windows boot loader to fix XP. what you need to do is get the disk you installed XP with (it has to be the same version and service pack) and boot it, when it gives you a menu, type R to repair windows. it will ask you what windows installation you want to repair, itll list them (if you have more than one, but ill assume you dont), just press 1 and then enter. if you have an administrator password, youll have to enter it now. now youll have a command prompt, type "fixmbr" without the quotes, itll say something about this could damage your partition table (and it may, but its EXTREMELY unlikely, in any case, i will not be held responsible) type "y" and then hit enter and its done. type "exit" and take the cd out, your computer is now rebooting

-Wild

---

### Post by soul on 2005-07-03
Thanks, that got Windows to work, but it completely erased my external harddrive. Oh well, I guess it was time for a fresh start :D 

I tried installing ubuntu again and this time I got an error message saying the grub loader couldn't be installed because of some error :( So now I'm stuck using the live CD again.

---

