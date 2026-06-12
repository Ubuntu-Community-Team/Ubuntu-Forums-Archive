---
title: "how can i upgrade BIOS with no floppy or no CD?"
date: 2008-03-23
forum: Installation &amp; Upgrades
---

### Post by setotitan on 2008-03-23
hey guys i've made the transition to linux from windowz but i'm running into a problem. i need to upgrade my BIOS but i have no floppy drive, no CD/DVD drive, and can't boot from USB. i've overcome many hurdles that i thought i was going to have to junk this computer over, but i'm really hitting a brick wall with this one. i found some thread about how to do however it was was specific to IBM thinkpad, and i'm using and ACER travelmate. anyone have any suggestions?

---

### Post by logos34 on 2008-03-23
That's a hard one...You would probably have to temporarily reinstall windows on a part of the hard disk in order to run the Winflash utility.  But even that's out of the question because you don't have a cdrom!

Do you really need to update the Bios?

---

### Post by logos34 on 2008-03-24
It just occurred to me that you could try running the Winflash program in linux on Wine.

---

### Post by setotitan on 2008-03-24
the only reason i was really wanting to do the upgrade is because every time i boot up my computer after GRUB but before the ubuntu login screen i get a black screen and this scrolls:


PCI : Cannot allocate resource region 6 of bridge 0000:00:1e.0
PCI : Cannot allocate resource region 7 of bridge 0000:00:1e.0
PCI : Cannot allocate resource region 8 of bridge 0000:00:1e.0
PCI : Cannot allocate resource region 9 of bridge 0000:00:1e.0

i can't seem to find any way to fix this. the only solution anyone had was updating your BIOS. i mean my computer is completely functional, i guess i'm just nit picking.

---

### Post by Loranga on 2008-05-07
> **logos34 said:**
> It just occurred to me that you could try running the Winflash program in linux on Wine.

Would that be safe?

---

### Post by Rhubarb on 2008-05-07
> **logos34 said:**
> It just occurred to me that you could try running the Winflash program in linux on Wine.
You can try it, but it won't work.
At the very best you'll be able to extract the files you need to flash, and put those file in a freedos image.

The best way I've found that works with a lot of BIOS upgrades (doesn't work with all, only those that'll work from a DOS environment):
[http://ubuntuforums.org/showthread.php?t=318789](http://ubuntuforums.org/showthread.php?t=318789)

---

