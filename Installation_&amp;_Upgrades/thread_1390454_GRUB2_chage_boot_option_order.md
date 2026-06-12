---
title: "GRUB2 chage boot option order?"
date: 2010-01-25
forum: Installation &amp; Upgrades
---

### Post by wlraider70 on 2010-01-25
My GRUB is working fine, but I want windows to be first on the list. How can i change it?

---

### Post by hhlp on 2010-01-25
follow this guide :

[https://wiki.ubuntu.com/Grub2](https://wiki.ubuntu.com/Grub2)

you have to view this part in this file :

grub (/etc/default/grub) and this parameters :

      GRUB_DEFAULT=0
          
            Sets the default and pre-selected menu entry. Entries may be numeric or saved
          
            GRUB_DEFAULT=0
                + Sets the default menu entry by menu position. As with Grub Legacy, the first "menuentry" in grub.cfg is 0, the second is 1, etc. 
          
            GRUB_DEFAULT="Windows XP Professional (on /dev/sda1)"
                + Sets the default menu entry by name. 
          
            GRUB_DEFAULT=saved
                + Sets the default menu entry with whatever was selected on the last boot. If the menu is displayed during boot, the previously selected option will be highlighted. If no action is taken, this is selection which will be booted at the end of the timeout, or if the menu is hidden. 
    *

---

### Post by drs305 on 2010-01-25
I think you want to change the *order* of your entries? If so, the easiest way is to add the menuentries into /etc/grub.d/40_custom and place them in the order you want them. Rename the file 06_custom so it displays at the top of the menu. Make sure the file is executable, then run "sudo update-grub".

The advantage is you can order them in any way you want. You can also change the titles between the quotes to anything. 

The disadvantage of this method is that the contents of 40_custom never get updated unless you do it manually.

Additionally, you will see your custom menu *plus* the automated entries. You can disable the automated entries such as the Windows entry by removing the executable bit from /etc/grub.d/30_os-prober.

I believe *meierfra* wrote a guide on building a custom script. I'll add the link as soon as I find it.

Added:  Here you go:
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Custom_Menu]("http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Custom_Menu")

---

