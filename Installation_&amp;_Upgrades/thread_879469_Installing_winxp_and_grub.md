---
title: "Installing winxp and grub"
date: 2008-08-04
forum: Installation &amp; Upgrades
---

### Post by rounder24 on 2008-08-04
I currently have a laptop running a dual boot (1 drive, seperate partitions) of win vista and ubuntu 8.04.

Having not liked vista so much I want to replace it with winXP again. Whenever I boot from the winXP disk, when it gets to the "checking system hardware screen" it goes black and halts there. 

I've tried multiple copies which work on other people computers. I read somewhere that if grub is installed in the MBR the winXP disk won't boot up properly. I'm guessing that is the cause. 

How can I fix this? I don't have a floppy drive because it's a new laptop but I could buy a usb one if that helps. And since it crashes at that screen I can't get to the recovery console to use the fixmbr command. 

Thanks for the help in advance.

---

### Post by rounder24 on 2008-08-04
bump

---

### Post by logos34 on 2008-08-04
> **rounder24 said:**
> I read somewhere that if grub is installed in the MBR the winXP disk won't boot up properly. I'm guessing that is the cause. 

How can I fix this? I don't have a floppy drive because it's a new laptop but I could buy a usb one if that helps. And since it crashes at that screen I can't get to the recovery console to use the fixmbr command. 


I've never had a problem with xp install disc and grub.  

Maybe you have a small vista recovery partition that could be blocking it somehow?

You could try using Gparted in ubuntu to wipe/delete the vista partition (and recovery if present), then run the xp install cd again and install in empty/unallocated space.  Since XP will overwrite grub on the mbr, you can restore the latter using the ubuntu live cd (see link below).

---

