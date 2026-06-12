---
title: "Install goes nowehere on old AMD system"
date: 2008-05-20
forum: Installation &amp; Upgrades
---

### Post by BelowGrade on 2008-05-20
I have verified the Md5SUM on my installation CD.  (8.04 LTS Server).  It works properly on my newish HP Athlon dual-core system.  But the system I want to put it on is a 6 year old Athlon with IDE disks and an ATI 7500 video card.

On that system, the CD boots and I pick the language.  Then I select "Install Ubuntu" from the menu.  The screen goes black with a blinking cursor at the upper left.

When I add " priority=low BOOT_DEBUG=2" to the boot command line I get the following repeated three times:
[FONT="Courier New"][: 2--: bad number[/FONT]

I have tried "fb=false" and "DEBIAN_FRONTEND=text" to no avail.  Clearly there is something about my hardware it doesn't like.  But my old software, some ancient Gentoo, still boots fine on it.

---

### Post by BelowGrade on 2008-05-20
I forgot to add that I do get the "Loading Kernel..." message.  It is after that when the screen goes blank.

I found an old 7.10 desktop disk and that get farther, then complains about timeout waiting for DMA, and finally proceeds with a normal install.  But I want the server config, not desktop, and the 8.04, not 7.10.

---

### Post by BelowGrade on 2008-05-20
Pressing F4 during install to select "Install mode" gives me a menu with just one choice: "NORMAL".

---

### Post by gkforcare on 2008-10-04
I'm in the same situation. It looks like ide is to slow somehow. It did work ok with Fedora Core 2 (old, yes, I know, not for nothing I want to install Ubuntu 8.04.1 LTS ;-) )

I did try to use ide=nodma, but to no avail. I reaeaeally want to get this baby going with Ubuntu... Maybe I should download an old Ubuntu version? (and upgrade...)

wkr,
Gerke

---

### Post by gkforcare on 2008-10-04
you know what did it in the end? It was a hardware 'failure' that was masked by the drive showing up in the BIOS with a very long delay but to slow for Ubuntu 8.04.1 and just fast enough for Fedora Core 2... Anyway, I fiddled with the master/slave jumper (good old times ;-) ) and now it's faster in startup and works in Ubuntu 8.04.1

wkr,
Gerke

---

