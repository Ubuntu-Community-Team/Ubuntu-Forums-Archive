---
title: "Automatic updates (kernals) - Should I do it or not ?"
date: 2007-06-06
forum: Installation &amp; Upgrades
---

### Post by paddyboy on 2007-06-06
Hi,
I have 7.04 and at the time of install the generic kernal was 2.6..20.15. After a bit of fiddling I got it to behave (added noapic to the grub boot line).
As you know recently the 2.6.20.16 generic was offered as an update. Maybe foolishly I installed it as a matter of course. I was then back to my original problem so I added 'noapic' and off I went.

My question is ....what was wrong with the old generic ? As I see it, if I continue to accept automatic updates (kernals) my boot menu (I'm a dual booter) will become unmanageablly large. 

What do you experienced guys do ? Do I keep my 2.6.20.16 and trash the 15 ? I've turned off automatic updates now until I know why they are needed and Is it safe to edit the /boot/grub/menu.lst ?

I'm pretty new, so simple suggestions would be most welcome.
Many thanks

---

### Post by Bachstelze on 2007-06-06
If the new kernel is running fine, you should be safe deleting the old one in Synaptic. However, it's always a good idea to keep at least two.

---

### Post by DerHesse on 2007-06-06
You can specify the amount of entries shown in the Grub menue, by editing /boot/grub/menu.lst .

There is al ot of comments, you will find it!
 Updates are updates. If you want to stay up to date leave the automatic updates.

---

### Post by paddyboy on 2007-06-06
Thanks for suggestions.

BTW is it ok to comment out the unwanted entries in the /boot/grub/menu.lst thus......

## title           Ubuntu, kernel 2.6.20-15-generic
## root            (hd0,2)
## etc

Safe ?

---

### Post by scradock on 2007-06-06
Perfectly safe - that's what I do. Comment them out like that for a few days, then delete them when I'm sure everything works OK....

---

