---
title: "Gnome3 'jibberish' graphics"
date: 2011-10-14
forum: Installation &amp; Upgrades
---

### Post by An Sanct on 2011-10-14
Hey all!

Well. Yesterday I installed the officially *ubuntu.com* launched version of desktop 11.10 64b downloaded via torrent (thus no CRC problems).

I installed Gnome3 from the software center and was surprised to see, that it had the same problems as in the beta version (I did not want to nag about it then, but do now...)

-fonts are missing, some characters are replaced with garbage, whilst some are fine
-borders are missing or made of garbage pixels (almost like invert)
-top panel is blurry, filled with random garbage pixels ...

This seems to be a single problem, can anybody tell me what went wrong? What am I missing?

PS. Wanted to make a snapshot, but that was not possible, all I got was my cursor and the wallpaper....

---

### Post by mastablasta on 2011-10-14
> **An Sanct said:**
> Hey all!
 
I installed Gnome3 from the software center and was surprised to see, that it had the same problems as in the beta version (I did not want to nag about it then, but do now...)

 
 
you mean Gnome Shell? Gnome 3 is already included in 11.10

---

### Post by An Sanct on 2011-10-14
Gnome shell then :) 

I installed it via SC.

(the thing, Linus calls an "*unholy mess*")

---

### Post by hsoulen on 2011-10-14
> **An Sanct said:**
> Hey all!

Well. Yesterday I installed the officially *ubuntu.com* launched version of desktop 11.10 64b downloaded via torrent (thus no CRC problems).

I installed Gnome3 from the software center and was surprised to see, that it had the same problems as in the beta version (I did not want to nag about it then, but do now...)

-fonts are missing, some characters are replaced with garbage, whilst some are fine
-borders are missing or made of garbage pixels (almost like invert)
-top panel is blurry, filled with random garbage pixels ...

This seems to be a single problem, can anybody tell me what went wrong? What am I missing?

PS. Wanted to make a snapshot, but that was not possible, all I got was my cursor and the wallpaper....

Can you share a bit more on your hardware? Are you using Nvidia/ATI/Intel for graphics? Are you using the Open Source or Proprietary drivers for your graphics chipset?

If it's ATI, there are a whole lot of issues with Gnome 3 shell and ATI graphics right now (Fedora problem but valid as this covers Gnome 3 in general):

[http://phoronix.com/forums/showthread.php?56264-Graphical-corruption-with-gnome-shell]("http://phoronix.com/forums/showthread.php?56264-Graphical-corruption-with-gnome-shell")

Cheers,

Hank

---

### Post by An Sanct on 2011-10-14
Took a dive into lshw and got this result:

PCI ATI Technologies Inc (PC Partner Limited) RV710 [Radeon HD 4350]

The drivers are proprietary. I selected one of two options in the "Additional Drivers" configuration window.

PS. I'm dual booting with Maverick, so Oneiric is just a test OS - no problem if it does not get fixed soon.

---

### Post by hsoulen on 2011-10-14
> **An Sanct said:**
> Took a dive into lshw and got this result:

PCI ATI Technologies Inc (PC Partner Limited) RV710 [Radeon HD 4350]

The drivers are proprietary. I selected one of two options in the "Additional Drivers" configuration window.

PS. I'm dual booting with Maverick, so Oneiric is just a test OS - no problem if it does not get fixed soon.

Yeah, you are one of the many at the moment where ATI is just not quite up to snuff.

Apparently they are working on a fix (AMD/ATI that is) and if I remember correctly Phoronix had an article testing it with some more positive results (can't seem to find the URL). So there is hope.

I would just keep checking back with AMD/ATI to see when they update their Linux drivers, or you could of course try the Open Source drivers as well.

Sorry I could not be of more help.

Hank

---

### Post by An Sanct on 2011-10-14
No problem, hank! Thanks for your time anyway ;)

---

### Post by An Sanct on 2011-10-14
Tried it without the proprietary drivers and it took me to Gnome3 2D :) a bad replacement for Gnome2... Well, cannot have it all ;)

Note to myself: Next time, consult the community, before buying a graphics card ...

---

