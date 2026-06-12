---
title: "Triple Boot"
date: 2008-07-30
forum: Installation &amp; Upgrades
---

### Post by anorrell23 on 2008-07-30
Hi, 
I recently installed three operating systems onto my custom pc in this order, so that the grub would show all three operating systems as options, but i made a mistake.

First i installed XP on a seperate IDE hd.
Then Vista on a 80 gig partion in a 160 gb Sata hd.
Ubuntu on a manual partition (largest empty space).

grub shows options for ubuntu and vista, b/c it did not search the ide for operating systems. Vistas bootloader installed to the ide so i can access every os but i have to go to boot options and boot from dif hd's for dif os's. Is there a way to add xp to the bootloader? or put the grub onto the ide wich already has the vista/xp?

---

### Post by Herman on 2008-07-30
I'll bet Vista's boot loader is actually in Windows XP.
If that's the case, if you ever get a virus in Windows XP you will lose both XP and Vista.
They do that to you deliberately and neglect to warn you about it.

You might be able to fix it but you'll need someone who's more of a Vista expert than I am to advise you.

Here's a good link, [Understanding MultiBooting and Booting Windows from an Extended Partition.]("http://www.goodells.net/multiboot/index.htm")
Here's another good link, [Multibooters - Dual/Multi Booting With Vista]("http://www.multibooters.co.uk/").

Neither of those links will help you directly, but if you have time to study up on your problem at least you'll be able to understand what actually happened.

None of it is Ubuntu's or GRUB's fault. 

Regards, Herman :)

---

