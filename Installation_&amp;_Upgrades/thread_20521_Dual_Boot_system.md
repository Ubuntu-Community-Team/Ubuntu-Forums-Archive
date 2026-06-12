---
title: "Dual Boot system"
date: 2005-03-17
forum: Installation &amp; Upgrades
---

### Post by oxinosch on 2005-03-17
Hello guys,

I have a dual boot and system with XP/Mandrake. What i would like to do now is to remove mandrake and install Ubuntu instead. What i would like to know if you guys think this is something hard for a linux beginner to do on his own , or should i get some help? Basic thing is that i dont want any surprises... I really need a working computer right now(i am working on my thesis at the time).

thnx

---

### Post by Xian on 2005-03-17
[QUOTE=oxinosch]I have a dual boot and system with XP/Mandrake. What i would like to do now is to remove mandrake and install Ubuntu instead. [/QUOTE]
This won't be any problem. Just reformat the partitions that Mandrake is on during the Ubuntu installation, set your desired mount points, and use the same swap file that's already present. Then be sure to install the bootloader to the MBR and NOT the root partition. It will pick up your XP and include it in the Grub login options.

That should do it.

---

### Post by Xian on 2005-03-17
Be sure to back-up anything you want to save from your Mandrake partitions, as when you reformat those for Ubuntu that data will no longer be accessible. Just post back with any problems, as you can back out of the installer at any time prior to writing to the disk and no changes will have been made.

---

