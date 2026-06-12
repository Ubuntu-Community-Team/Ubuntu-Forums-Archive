---
title: "Menu.1st fix?"
date: 2008-08-29
forum: Installation &amp; Upgrades
---

### Post by Mic_Droz on 2008-08-29
Hey guys, i've noticed my kernels on the startup screen have stopped updating... ie.19 hasn't shown up when I clearly spend a million years downloading it

do you think its safe to delete the menu.1st file, then run grub-update to start again afresh?

seems like a winner to me, but hey, what do I know?

---

### Post by louieb on 2008-08-29
should not have to delete menu.lst. If you want you could rename it. At the least make a backup copy of it. 

you could just run 
```
sudo update-grub
```
 and see what happens

Did you check /boot to see if vmlinuz-2.6.24-19-generic exist?

Worse comes to worse you could just add the entry yourself.

as a final note update-grub is controlled by several options found in the menu.lst file. see man update-grub for more information.
Good Luck.

---

### Post by Mic_Droz on 2008-08-31
Hey, thanks for the reply.

sorry, i should have clarified a little more... I'd already tried running the update command with sudo - it said it updated the menu.1st, but clearly the booting procedure wasn't update. 

I did delete the menu.1st file, ran update-grub, and presto, -19 is now working. shame about it breaking my wireless though. 

*sigh*

I think i'll look around for answers before I ask again - i think its got something to do with my Atheros HAL layer, and the fact that it isn't there, which is the only difference between -19 and -18.  

onward and upward, eh?

---

