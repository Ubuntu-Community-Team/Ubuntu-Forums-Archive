---
title: "Oh so helpless and grubby"
date: 2007-03-25
forum: Installation &amp; Upgrades
---

### Post by carlitoboss on 2007-03-25
Hi
So im in a bit of a tangle..

I have 2 hard drives an 80 gig IDE and 250 SATA..

IDE is set to primary boot
Has windows installed on it
SATA has a partition on it with a Kubuntu install
I have also managed to get another kubuntu install stuck somewhere.

When i start my PC in the GRUBB menu it has 2 kubuntu and the windows.. which wont load and stays on  "starting..."
Kubuntu loads..

I dont understand why it doesnt load windows if its set to primary boot/why windows wont load from the menu and why if i remove the sata i get a grub error 21 sometimes 22... GRUB must of stuck himself somewhere on the IDE..

help? without having to fixmbr just yet

---

### Post by daynah on 2007-03-25
I don't know if the grub is on both harddrives, or more similar to a bios (you know, just in the ether ;) ). But if it didn't show up if you had windows on your primary boot, then what about the noobs who forgot to set ubuntu drive as their primary boot? we'd get a zerg rush on the forums saying that they spent all that time installing ubuntu and it doesn't even load.

Would it help you to reorder the grub so that windows was on top?
[http://ubuntuforums.org/showthread.php?t=392722&highlight=boot+windows+grub](http://ubuntuforums.org/showthread.php?t=392722&highlight=boot+windows+grub)

Like in that? Otherwise, I don't know how you'd get back to Ubuntu if you got rid of the grub (except by having to get the grub back...)

I also found this, which still uses the grub but may be more what you're asking for (just changing the order around in the grub) but it doesn't give very good directions...

[http://ubuntuforums.org/showthread.php?p=2249187](http://ubuntuforums.org/showthread.php?p=2249187)

---

### Post by carlitoboss on 2007-03-26
well, even though ubuntu is my first choice on the list, windows wont work when i load it, also.. i think grubb is on both drives..

---

