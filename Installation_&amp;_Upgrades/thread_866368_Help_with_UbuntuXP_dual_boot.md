---
title: "Help with Ubuntu/XP dual boot"
date: 2008-07-21
forum: Installation &amp; Upgrades
---

### Post by Jauggernaut on 2008-07-21
I have installed ubuntu 8.04 Hardy on my new PC and i would like to dual boot with windows xp, but the problem is that when i try to install xp to my SATA II hard drive it wont install i heard that you need 3rd party repositories or something like that and you need to install those through a floppy drive, how ever, I dont know where to get the repositories or how to install them without a floppy drive since i dont have one. If you could please help me, that would be greatly appreciated.

---

### Post by logos34 on 2008-07-21
Maybe Sata mode 'AHCI' is enabled in the Bios.  Try changing it to ide emulation or legacy mode

---

### Post by fmartinez on 2008-07-21
Usually on a dual boot you want to: 
- install XP where it will be stored. 
- Then install Linux and let it write the to the MBR where it will find the XP partition and give you and entry in the grub menu to boot from. 
- That's easiest way. if this is a fresh installation of linux this maybe the route you may want to go. 
It's never failed and i've done several DB's with this setup. 
Good Luck.

---

### Post by upchucky on 2008-07-21
It seems that you have installed ubuntu first? if so you must install windows first then ubuntu.
Due to the world domination mindset of the redmond gang, they will not let another os coexist.

Linux however is more forgiving and lets others play in the sandbox too.

you may have grub errors when you are done, search for possible solutions in case it wont boot when done, grub is easy fix if you are armed with the right info.

---

### Post by logos34 on 2008-07-21
You don't have to install windows first and reinstall ubuntu (you can simply [restore grub this way]("http://ubuntuforums.org/showthread.php?t=224351")).  But unless you've done a lot of personalized settings and configuration, it would probably be better/faster to backup saved files and reinstall ubuntu.

---

### Post by Jauggernaut on 2008-07-21
> **logos34 said:**
> Maybe Sata mode 'AHCI' is enabled in the Bios.  Try changing it to ide emulation or legacy mode

Cool, thx ill try that :D

---

