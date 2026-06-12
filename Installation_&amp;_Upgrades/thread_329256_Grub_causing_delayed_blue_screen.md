---
title: "Grub causing delayed blue screen?"
date: 2007-01-01
forum: Installation &amp; Upgrades
---

### Post by diverdale on 2007-01-01
So I installed Edgy in a dual boot config. XP has been working fine. Now when I boot into XP, after a while whether I'm doing anything or it's just sitting, I get a blue screen. Also of note, XP won't launch the screen saver now. This happened a while back with Breezy but I had been running the same install of XP for a couple years and I just chalked it up to bad install, or whatever. This is a fairly new install and HD (couple months) and I get the EXACT same problem. That's why I think it has to be a grub problem. Any ideas?

---

### Post by gn2 on 2007-01-01
What does it say on the blue screen?

---

### Post by diverdale on 2007-01-01
0x00000077  Kernel_Stack_Inpage_Error  M$ says that it happens when you have an infected mbr....so how do I fix this? It's not infected, it's healed :)

---

### Post by gn2 on 2007-01-01
To repair mbr, insert Windows CD and re-boot. Run "fixmbr" from Recovery.

This will write you a new mbr.

You will then need to re-install Grub: [http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/), 
or find an alternative bootloader: [http://gag.sourceforge.net/](http://gag.sourceforge.net/) 

I prefer to have a dual-boot on two drives, this stops conflict between OS's
More info here: [http://www.ubuntuforums.org/showthread.php?t=275728](http://www.ubuntuforums.org/showthread.php?t=275728)

---

