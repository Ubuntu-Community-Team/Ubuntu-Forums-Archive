---
title: "floppy + no bootloader"
date: 2005-04-12
forum: Installation &amp; Upgrades
---

### Post by el_chupanegre on 2005-04-12
This is a little bit of an odd request i realise before i even explain but ill try anyway :)

I currently have WinXP installed, and i wish to install ubuntu. 'Wheres the problem?' right? :) The thing is, ive installed ubuntu before (as well as countless other distros) a couple of times (but its not installed at the moment, only WinXP) and im basically sick of having a bootloader with a choice (whether is be lilo or grub).

My question really is, can i install ubuntu (5.04) without any bootloader, so that when i switch my comp on, it goes straight into WinXP as if ubuntu wasnt there. However, when im in my more adventurous of moods :) i have a floppy disk, which i put into the comp and boot, and that boots into ubuntu as if theres no WinXP (so i dont mess with the MBR is any way). I only really use linux for experimentation and to get a feel for it and i dont feel confident enough to drop WinXP just yet, so the fact i get asked every time i boot which OS id like annoys me. id just like a floppy that i use when i want ubuntu, and i dont use when i want WinXP.

Thanks for your time and any suggestions.
el_chupanegre

---

### Post by alastair on 2005-04-12
Do an "expert" mode install (this might not need "expert") and install the bootloader to the floppy device when prompted (NOT to the disk).

---

### Post by el_chupanegre on 2005-04-12
ok i think i get that, just a few questions:

1. does the floppy need to have any special formatting or anything?
2. ive never done an expert install, so i assume its not much more difficult than the normal one?
3. it would ask my where to install to, would i type /dev/fd0 or is there some kind of drop down menu or something?

thanks,
el_chupanegre

---

### Post by alastair on 2005-04-13
1. No special preparation
2. Not very hard - it prompts you for a few more things and has a menu of steps to walk through
3. I can't remember! But it was not hard - I think you first have to choose to NOT install GRUB (to hard disk) - it then prompts you for a bootloader location

---

