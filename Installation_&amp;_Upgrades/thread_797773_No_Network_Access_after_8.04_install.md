---
title: "No Network Access after 8.04 install"
date: 2008-05-17
forum: Installation &amp; Upgrades
---

### Post by CometCKO on 2008-05-17
Live CD had internet access, but after install, my ethernet network adapter was not detected.  is there a way I can force it to detect?

Longer story.  This was working successfully with Dapper Drake.  I had once before installed 8.04 and successfully had internet with this same install disk.  Something flaky here.  I'll try to install again and see if next time it works.

I'll also try the alternate install disk, if I can find a computer with a writer so I can burn a disk (my laptop has no burner).

Thanks for any suggestions on how to detect/install.

Hardware is Athlon Xp3000+/Epox 8rga mobo; integrated NVIDIA graphics card, Nvidia onboard ethernet

---

### Post by Pumalite on 2008-05-17
Open up all your repos and do:
sudo apt-get update
sudo apt-get upgrade
If still having problems; post back.

---

### Post by CometCKO on 2008-05-17
OK, this can be chalked up to "pilot error"

Apparently, when I updated the BIOS in my computer to boot from my USB drive, somehow the switch for the network adapter was turned off.  So from the software standpoint, there WAS NO Network adapter. (sigh :( )

This is where the text-based alternate installer is more helpful than the graphic one: it turned the screen red when it discovered no NIC.  I said "of course it has a NIC" but I was wrong...

Anyway, I recommend the alternate installer over the standard one for Hearty Heron!

Thanks for your help!

DF

---

