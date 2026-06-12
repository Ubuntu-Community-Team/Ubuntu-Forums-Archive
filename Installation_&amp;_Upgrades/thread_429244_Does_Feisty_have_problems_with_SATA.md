---
title: "Does Feisty have problems with SATA?"
date: 2007-05-01
forum: Installation &amp; Upgrades
---

### Post by jrohde on 2007-05-01
Hi,

I can't install Feisty on my DELL Dimension 9150. It craches with a kernel panic a few seconds after having startet the boot process from the initial menu. I get this dump:

[IMG]http://i174.photobucket.com/albums/w91/jakobrohde/screenshot.jpg[/IMG]

I have tried both he desktop edition and the alternate cd. I have tried to remove all external equipment, such as USB disk and bluetooth USB-stick.

I have been googling around, and I suspect SATA to be the reason, but I'm not sure.

Any help would be appreciated.

Thanks

Jakob

Ps. Yes, this is my second post on the same topic. I thought that maybe if I refrased my question, I might get lucky and get a response...

---

### Post by Syke on 2007-05-01
So you can boot the Live CD fine, it's just installing to your drive that crashes?

---

### Post by jrohde on 2007-05-01
Hi Syke,

I'm not sure what the name of the menu is, but the crash occurs after having startet the boot process from the initial menu (the first menu you get after booting the CD).

So, no, I cannot boot the Live CD.

Jakob

---

### Post by wislon on 2007-05-01
Have you tried doing a search on the forum for 'kernel panic'? I ran into similar issues with Edgy not liking my power management stuff on the board (acpi), giving me a very similar error. I put 'acpi=force' into my grub boot entry, and that fixed it, but obviously YMMV. There'll be other solutions out there, you're definitely not the first person to have this, and definitely won't be the last! :\

---

### Post by jrohde on 2007-05-01
> **wislon said:**
> Have you tried doing a search on the forum for 'kernel panic'? 

Yes I have. But unfortunately the phrase "kernel panic" occurs quite often ;-) And I haven't been able to find anything similar to my problem. But I suspect it has something to do with SATA. I have Windows Vista on the other disk, so before taking any risks with the BIOS settings, I prefer to be sure what causes my problem.

Jakob

---

