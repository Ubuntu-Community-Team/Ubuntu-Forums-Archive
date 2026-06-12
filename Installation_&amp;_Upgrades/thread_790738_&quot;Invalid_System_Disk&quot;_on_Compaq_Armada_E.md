---
title: "&quot;Invalid System Disk&quot; on Compaq Armada E500"
date: 2008-05-11
forum: Installation &amp; Upgrades
---

### Post by rizlmilk on 2008-05-11
I recently got a Compaq Armada E500 from a friend for $10. The reason he stopped using it, and decided to sell it to me, was because it had a Windows XP install infected so badly that it hardly booted. Since I got it, I've gotten it run XP pretty nicely but there are still random IE popups and other things that are obviously parts of the old viruses (which are probably still there).

So I've decided that I want to install Ubuntu, as I hate Windows anyway, but when I try to boot the live cd, alternative cd, or any other distro, I get a message saying:

"Invalid system disk
 Replace the disk, and then press any key"

I know the cd isn't defective, as I've tested it on other machines.
I'm not exactly sure what this means, or what I need to do to fix it. I would prefer sticking with a cd install, as I've done it plenty of times before. Also, the computer doesn't have a LAN/ethernet port just a wireless card, so any alternatives to install that need an internet connection are probably out of the question.

Thanks for any help.

---

### Post by rizlmilk on 2008-05-12
I just updated the bios, thinking it might help with booting from the cd drive, but that doesn't seem to have done anything.

Does anyone know anything I can do to make this computer boot from a cd correctly?

---

### Post by Gallienus on 2008-05-16
You say that you updated your BIOS. I understand this to mean that you downloaded a more recent BIOS from the internet and replaced your old BIOS with this new one. However, you will almost certainly still need to adjust your BIOS settings, as they may not be set to boot from a CD by default. Open up your BIOS and look for an option named 'boot sequence' or something similar. Then change it to make sure that you are booting from the CD before the hard disk.

---

