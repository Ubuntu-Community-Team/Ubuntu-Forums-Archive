---
title: "Install Ubuntu and Mepis - 2 Hard Drives"
date: 2008-01-04
forum: Installation &amp; Upgrades
---

### Post by JawsThemeSwimming428 on 2008-01-04
I just purchased a brand new Western Digital Caviar 160GB. I already have a 40GB Western Digital Caviar in the system. I used Ubuntu for about two years and had some trouble with it recently so I was trying out Mepis. I like Mepis as much as I used to like Ubuntu. Mepis is currently installed on both drives, but I would like to install Ubuntu on the 40GB to use. My question is how do I set it up so that I can dual boot (when the Mepis GRUB screen comes up I want to be able to pick Mepis or Ubuntu)? They are both SATA drives.

---

### Post by logos34 on 2008-01-04
Go into the Bios and set the 40 gb drive first in the hard disk boot priority.  Make sure it is also connected to Sata port 1 on the motherboard (to assure grub designates it as 'hd0').  Install ubuntu.  The ubuntu ubiquity installer and/or grub should detect Mepis and add it to menu.lst so you have a choice of OS's at boot.  If for some reason it doesn't detect Mepis, you can [add it manually.]("http://users.bigpond.net.au/hermanzone/p15.htm#Operating_System_Entries_for_Multiple_Booting_More_Linux_Systems")

---

### Post by JawsThemeSwimming428 on 2008-01-05
I want to use the Mepis GRUB screen though. GRUB is installed on my 160GB drive. If I do what you said won't it use the Ubuntu GRUB screen?

---

### Post by louieb on 2008-01-05
You can do it just the way you want. When you install Ubuntu have it put the GRUB pointer in the boot sector of its root partition. Look for the advanced button before the install begins (you will have to learn a little GRUB speak - the site logos34 linked to has a good explanation of how GRUB  refers to partitons ).

 After Ubuntu is install you need to add Ubuntu to the Mepis GRUB menu to. I recommend you use the **configfile or chainloader option**.  Again the Dual Boot Site has all the information you need to get set up just the way you want. [Illustrated Dual Boot Site]("http://users.bigpond.net.au/hermanzone/")

---

