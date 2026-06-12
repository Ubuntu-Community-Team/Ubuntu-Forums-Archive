---
title: "Trying to install 7.10 but problems with GRUB"
date: 2007-10-25
forum: Installation &amp; Upgrades
---

### Post by guiltyfart on 2007-10-25
I can't install 7.10 with GRUB but if i dont install it I cant boot into it, its goes to xP, i tried to use acronis boot loader but it wont load...

I just need to find out what i put in on the advanced tab for the install hd for the GRUB install place because (hd0) doesnt work even though its the only hd in there... for the install i used dev/hdb5 and i tried hdb5 as well....

Total noob help is much appreciated

---

### Post by granz on 2007-10-25
you could always edit the Windows bootloader to add Linux and use that ...
[http://piffle.mossiso.com/archives/22](http://piffle.mossiso.com/archives/22)

it's an option  :-

---

### Post by guiltyfart on 2007-10-25
Thanks trying that now

---

### Post by guiltyfart on 2007-10-25
I dunno..

Is there anything easier??? 

I really just need to get grub to install correctly

---

### Post by guiltyfart on 2007-10-25
I might have just figured it out....

---

### Post by guiltyfart on 2007-10-25
nope... I just need to figure out what to friggen put in the advanced tab for the grub install.... what partition thing to put it on..


the partition is /dev/hdb5 and the default is hd0

so what do i put in the spot

---

