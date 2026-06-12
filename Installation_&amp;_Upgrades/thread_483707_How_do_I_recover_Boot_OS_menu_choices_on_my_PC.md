---
title: "How do I recover Boot OS menu choices on my PC?"
date: 2007-06-25
forum: Installation &amp; Upgrades
---

### Post by intricate on 2007-06-25
Hello...I had to re-install WIN XP Pro on my dual boot hard drive which also contains FF 7.04 on the hard drive on a 2nd partition. When I re-installed XP, the boot menu that used to show FF 7.04 or XP Pro as boot choices when the PC first boots up disappeared. The PC just boots directly into WIN XP. 

How do I recover the menu which lets me choose which OS to boot into?

Thanks geniuses!

---

### Post by mikewhatever on 2007-06-25
Reinstalling XP removed Grub from the mbr, so now you'll need to put it back. This can be done using Ubuntu install (live) CD. [http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD](http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD)
I think it is also a good idea to copy the current menu.lst to some external storage device to have the entry for Windows for the new menu.lst

---

