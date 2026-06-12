---
title: "Can't boot with 8500GT"
date: 2007-09-09
forum: Installation &amp; Upgrades
---

### Post by ElGenerale on 2007-09-09
Hello all,

I'm building an HTPC running on Ubuntu. I've got a Gigabyte GA945GCM-S2 uATX board with on-board graphics, but I've got an EVGA 8500GT for TV-out. The problem is, when I try to boot with that card installed, the bios rolls by just fine but Ubuntu itself doesn't seem to recognize the card at all. It looks like it's booting okay, the hard drive light goes for a while like it's booting normally, but the screen just goes blank like there's no input. If I take the card out and use the on-board graphics everything works fine. If I try to use the on-board graphics when the card is in, I get nothing, like it's using the card like it's supposed to except there's nothing coming out of the card.

Is there some config file I have to edit somewhere, or something else I'm missing?

Thanks,

El Generale

---

### Post by Pumalite on 2007-09-09
I don't know if this could help:

[https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)

---

### Post by Pumalite on 2007-09-09
Sorry,

[http://ubuntuforums.org/showthread.php?t=542435](http://ubuntuforums.org/showthread.php?t=542435)

[http://ubuntuforums.org/showthread.php?t=542553](http://ubuntuforums.org/showthread.php?t=542553)

[https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.22/+bug/120943](https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.22/+bug/120943)

---

### Post by ElGenerale on 2007-09-09
I'm pretty sure it's not a driver issue, or if it is I'm truly screwed because I can't install the driver without the card in the box, and when the card is in the box the display doesn't work at all so I can't get to the driver install. By the same token, I can't do any diagnostics whatsoever with the card in the box. As near as I can tell the motherboard doesn't have the option to disable the on-board VGA, so I can't really tell if it's a conflict between the two graphics modules or a problem with the 8500GT itself. It really seems to have me stuck.

---

### Post by Pumalite on 2007-09-09
Me too. I wish I could help you. Maybe someone that knows better will chime in.

---

### Post by mav8989 on 2007-09-16
I have the same MB and a PNY GeForce 8500GT.  The difference in the cards aside, I noticed that you said you didn't think you could get the BIOS tweaked... I'd give you an exact location, but I can't drop the box thats got the Gigabyte MB in it.  However, I recall a setting that said something like "primary video" where you could either force the onboard chipset or "prefer" a PCI/PCIe card if found... Try forcing to onboard video and then running some diags in Ubuntu.  I'm no expert, but even though you use the onboard chipset, I don't see why Ubuntu wouldn't also see the BIOS on the card if it is plugged in.  I could be COMPLETELY WRONG though - BIOS stuff is NOT my thing... Check the BIOS again...

---

### Post by Pumalite on 2007-09-16
[http://samiux.wordpress.com/2007/06/15/geforce-8500gt-on-ubuntu-704/](http://samiux.wordpress.com/2007/06/15/geforce-8500gt-on-ubuntu-704/)

[http://ubuntuforums.org/showthread.php?t=547187](http://ubuntuforums.org/showthread.php?t=547187)

[http://ubuntuforums.org/archive/index.php/t-465280.html](http://ubuntuforums.org/archive/index.php/t-465280.html)

[http://www.mepislovers.org/forums/showthread.php?t=8802](http://www.mepislovers.org/forums/showthread.php?t=8802)

[http://www.mepislovers.org/forums/showthread.php?p=71205](http://www.mepislovers.org/forums/showthread.php?p=71205)

[http://www.phoronix.com/forums/showthread.php?t=2541#post7569](http://www.phoronix.com/forums/showthread.php?t=2541#post7569)

---

