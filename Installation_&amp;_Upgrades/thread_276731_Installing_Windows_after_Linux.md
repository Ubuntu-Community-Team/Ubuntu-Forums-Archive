---
title: "Installing Windows after Linux"
date: 2006-10-13
forum: Installation &amp; Upgrades
---

### Post by Hyakutaro on 2006-10-13
I am running Dapper on a 200 GB HDD, now I need (this sucks) to install Windows for my brother who occasionally play some Windows games... I have another 20 GB HDD. Could anyone give me some tips and advice on how to install XP (boo!) on my other hard drive without affecting Ubtuntu?

Thanks :)

---

### Post by Kateikyoushi on 2006-10-13
You can remove the ubuntu hdd and intall windows to the smaller drive and put back ubuntu to choose which OS to boot you have to select when your pc starts up. By pressing F8 or F12 depends on your BIOS.

You can install windows while ubuntu is in the pc that way you have to resintall grub because windows will overwrite it. To do this follow [this guide.]("http://doc.gwos.org/index.php/Restore_Grub")

If one drive is PATA the other is SATA then you might run into a bug, in that case selecting from the bios is recommended.

---

### Post by TheWizzard on 2006-10-13
> I need (this sucks) to install Windows for my brother who occasionally play some Windows games
what's the need? tell him to by an x-box. 
can't you run his games with wine? i don't have much experience with this, but most (not the newest) games are suppost to be able to run with wine.

---

### Post by meng on 2006-10-13
Here's another link explaining how to recover GRUB.
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)
I wouldn't trust wine to run most games/applications. Cedega maybe.

---

### Post by Hyakutaro on 2006-10-13
Well actually we already have 2 PS2s (the big fat black one which doesn't work well anymore and a silver PStwo)... we ARE NOT getting another console now :P

Some of these games run with WINE, but they run like crap... of course I can tell my brother to STFU and go to his room :P but I'm trying to be a nicer, better person :P

---

### Post by Kateikyoushi on 2006-10-13
If you really want to be a nice and better person buy him a PS3. ;)

---

### Post by K.Mandla on 2006-10-13
> **Hyakutaro said:**
> I'm trying to be a nicer, better person :P
:D

I think this can be done -- the idea of installing Windows after Ubuntu. I've never actually done it myself, though. So consider yourself among the few. ;)

Basically, if you open up space on your drive (via the GPartEd live CD or what have you), you can use that partition when you install Windows.

XP (being selfish) will reclaim the MBR, which means your Ubuntu partition will "disappear." Don't panic. ;)

Then you restore Grub to the MBR and add the Windows partition back in. Here are some threads that describe the last part ...

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

Good luck! And remember, back everything up first. It's very easy to lose everything when you're tweaking like this.

---

### Post by Hyakutaro on 2006-10-13
A PS3? HELL NO! Too damn expensive, and I don't game... :p

Thanks for your tips guys, I'll give it a shot :)
Alternatively I could tell my bro to go read a book instead of playing some video game... damn kids

---

