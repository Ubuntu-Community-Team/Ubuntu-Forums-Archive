---
title: "I lost my largest partition!!!!! HELP!!!!"
date: 2007-07-26
forum: Installation &amp; Upgrades
---

### Post by Tag_yer_dead on 2007-07-26
hey guys, big problem here lol.
My little sister got my computer a virus so me being the nerd i am, took it as an opportunity to reinstall and start over.  I dont like Vista very much so i thought, ill install vista on 150 gb, 75 for xp (gamse are better), and 20 for ubuntu.  I installed vista, partitioned everything correctly, and then installed xp.  I can see both are there, but GRUB only lets me see the XP partition. PLEASE HELP.  

My guess is editing the grub.txt file so that it finds it? but i dont know what to change exactly

---

### Post by jgfoot on 2007-07-26
Does /boot/grub/menu.lst have an entry for each operating system on your newly partitioned drive?  If not, edit it; there's an example in there, in the comments, for how to set up an option for a Windows partition.

---

### Post by mikewhatever on 2007-07-26
May I ask why you gave Vista 150 BG if you do not like it very much. On this scale, I suppose you really detest Ubuntu with its 20 GB.
The good news are, you have not lost any of the partitions. Your Vista is on the HDD and a quick search should solve the issue with the Grub entry for it.
Here you go [http://apcmag.com/5045/how_to_dual_boot_vista_with_linux](http://apcmag.com/5045/how_to_dual_boot_vista_with_linux)

---

