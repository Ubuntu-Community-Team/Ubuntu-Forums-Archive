---
title: "Too much Ubuntu? (Lots of boot options)"
date: 2006-09-11
forum: Installation &amp; Upgrades
---

### Post by Old Pink on 2006-09-11
Ok, when I first installed Ubuntu I had 3 options upon starting up: 

Ubuntu, Kernel xxxxxxxxxxxxxxxxxxxxx
Ubuntu, Kernel xxxxxxxxxxxxxxxxxxxxx (recovery mode) 
Windows XP Professional 

Now I have 5 options (after updating the system): 

Ubuntu, Kernel yyyyyyyyyyyyyyyyyyyyyyy
Ubuntu, Kernel yyyyyyyyyyyyyyyyyyyyyyy (recovery mode) 
Ubuntu, Kernel xxxxxxxxxxxxxxxxxxxxx
 Ubuntu, Kernel xxxxxxxxxxxxxxxxxxxxx (recovery mode) 
Windows XP professional

However, the yyyyyyyyyyyyyyyyyyyyyyy selections are older versions of ubuntu, is there any way I can remove them, and just keep the yyyyyyyyyyyyyyyyyyyyyyy and XP options? :-k

Thanks
- Matt

---

### Post by ciscosurfer on 2006-09-11
You can comment out (by placing a pound sign #) the word "title" within your [COLOR=DarkRed]/boot/grub/menu.lst[/COLOR] file, which will effectively "hide" those kernel options in your boot menu.  It is sometimes advisable to keep them there anyway to allow yourself to easily revert back to an earlier kernel if you have problems with your new, updated kernel.

---

### Post by Old Pink on 2006-09-11
EDIT: Got it, now how do I log in as root? :confused:

EDIT2: Done, rebooting. :rolleyes:

---

### Post by ciscosurfer on 2006-09-11
So, instead of your normal title, and kernel line, etc., you want it to look like this, simply commenting out the 'title' line:

[COLOR=Sienna]#title          Ubuntu, kernel 2.6.15-23-386[/COLOR]

doing this will 'hide' it from your boot menu (you only need to comment out the 'title' line, all other lines you can leave as they are.

---

### Post by Old Pink on 2006-09-11
Thanks, all done, rebooting now. :D

---

### Post by ciscosurfer on 2006-09-11
I would advise against logging in as root (you first need to 'enable' the root account..you can search the forums on how to do this and other suggestions about the reasons why/why not to enable root).  When you need to superuser priveleges, you can use 'sudo' or 'gksudo' (for graphical apps requiring root priv's) or 'kdesu' if you're using KDE.

---

### Post by Old Pink on 2006-09-11
Thanks, I got sorted, rebooted, looks better. :) 

However, are these older versions hogging memory?

---

### Post by ciscosurfer on 2006-09-11
No, they aren't hogging any memory.  They reside in your /boot directory and just sit there unless they are utilized.

---

### Post by Old Pink on 2006-09-11
Nice... :) Thank you!

---

