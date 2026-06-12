---
title: "Upgrading from Warty to Hoary"
date: 2005-05-28
forum: Installation &amp; Upgrades
---

### Post by kjmorris on 2005-05-28
I have Warty installed on my laptop (Dell Inspiron 1150 Celeron). I just downloaded the Hoary iso and burned it to a CD. I would like to use it to upgrade from Warty to Hoary. I set the laptop to boot first from the DVD/CDRW drive but nothing happens. (I assumed that it would boot the CD and ask me to choose between a cold install and an upgrade).

I would appreciate some instructions on how to proceeed or being directed to a a how-to document.

TIA  kjmorris

---

### Post by tread on 2005-05-28
boot into warty as usual, and then pop in the cdrom.
If ubuntu doesnt automatically detect it as a packages cd and prompt you for the next step, start a terminal and run

sudo apt-cdrom add

This will add the dvd to your sources.list, and you can run synaptic, update the package list and upgrade.

---

### Post by Stefan Koopmanschap on 2005-05-29
[QUOTE=tread]boot into warty as usual, and then pop in the cdrom.
If ubuntu doesnt automatically detect it as a packages cd and prompt you for the next step, start a terminal and run

sudo apt-cdrom add

This will add the dvd to your sources.list, and you can run synaptic, update the package list and upgrade.[/QUOTE]
 ok, I downloaded the Hoary cd rom, burned it, but for some reason it can't mount the cdrom. now I could of course mount the iso itself, but is it easy to add a local repository to the sources.list?

---

### Post by Stefan Koopmanschap on 2005-05-29
reconsidering, would it also be possible to simply edit the sources.list to use the hoary repositories instead of the warty repositories, and upgrade using synaptic? would that work?

**update:** found the solution in the [warty user guide](http://ubuntuguide.org/4.10/index.html#upgradewartytohoary) ... I can just upgrade using the new sources.list entries :)

---

### Post by wallijonn on 2005-05-29
[QUOTE=kjmorris]I have Warty installed on my laptop. I just downloaded the Hoary iso and burned it to a CD. 

I would like to use it to upgrade from Warty to Hoary. 

I set the laptop to boot first from the DVD/CDRW drive but nothing happens. (I assumed that it would boot the CD and ask me to choose between a cold install and an upgrade).[/QUOTE]

Does the CD mount when Warty is up? If not, you may need to download & burn the image again.

Burn all your data (bookmarks, email, documents, downloads, etc.) before installing Hoary as it will overwrite the whole disk (one option, as I don't know if you have a dual boot. If you have a dual boot with WXP -  then that could be the reason why 'nothing happens'. ).

---

### Post by kjmorris on 2005-05-29
Thanks for the tips. I followed the Guide and successfully upgraded to Hoary.

However, upgrading did not accpmplish what I had hoped: solving the problem of screen resolution being limited to 640 x 480 - making th elaptop only minismally usable. I'll have to try a new thread again.

Thanks.  kjmorris

---

