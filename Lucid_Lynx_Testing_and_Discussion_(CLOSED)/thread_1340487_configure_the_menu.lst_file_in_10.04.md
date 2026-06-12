---
title: "configure the menu.lst file in 10.04"
date: 2009-11-28
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Papillonrus on 2009-11-28
How or where do you configure the menu.lst file in Lucid 10.04?

---

### Post by ibuclaw on 2009-11-28
I don't know where you have been for the past 3 months, but Ubuntu has switched to using Grub2. Since 9.10 hit alpha.

There no longer is a menu.lst

Instead, you edit the file:
```
/etc/default/grub
```
And run:
```
sudo update-grub
```
for the changes to take affect.

Regards
Iain

---

### Post by Papillonrus on 2009-11-29
I've been stuck in a Windows environment for the last year, because it is the OS of choice for classwork.

---

### Post by Papillonrus on 2009-11-29
How do I edit /etc/default/grub to boot to the windows XP os first?

---

### Post by ronacc on 2009-11-29
check this thread from the karmic (9.10) forum to start getting up to speed on grub2 . [http://ubuntuforums.org/showthread.php?t=1285897&highlight=grub2](http://ubuntuforums.org/showthread.php?t=1285897&highlight=grub2)

---

### Post by kansasnoob on 2009-11-29
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

Less reading and more specific:

[http://ubuntuforums.org/showthread.php?t=1302743&highlight=grub2+common](http://ubuntuforums.org/showthread.php?t=1302743&highlight=grub2+common)

---

### Post by ronacc on 2009-11-29
look at /boot/grub/grub.cfg and find the entry that you want to boot by default . note what number entry it is (remember to count from 0 ) and then change the line in /etc/default/grub which reads GRUB DEFAULT=0 to that number . then run ```
sudo update-grub
```

---

### Post by garvinrick4 on 2009-11-29
Try GUI Startup-Manager. Install it if you do not have it and
change your default operating system from boot tab.

---

### Post by autocrosser on 2009-11-29
That's not the best answer right now---SUM is in re-write to fully work with Grub2--not recommended until the developer gives a "thumbs up" on it.....

---

