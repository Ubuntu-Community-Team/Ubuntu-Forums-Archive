---
title: "Already have Breezy, now i want Dapper too..."
date: 2006-04-08
forum: Installation &amp; Upgrades
---

### Post by renzokuken on 2006-04-08
Ive been using breezy for about 6 months now and really happy with it, it is the sole OS on my PC.

well now im feeling quite confident in linux and i want to add Dapper as a second OS.

Currently breezy uses the whole of my sata drive. I will be creating a free partition on that disk to install Dapper onto.

My question is, what happens about GRUB?

Will the dapper install be added to my current GRUB list?

Or do i have to do some fiddling?

---

### Post by K.Mandla on 2006-04-08
I haven't done a Breezy-Dapper dual boot, but I would expect it to configure GRUB in the same way it does with any other multi-OS boot. I think you're safe to try it.

---

### Post by renzokuken on 2006-04-08
so will dapper detect the breezy install and change the GRUB in the MBR for me?

doesnt some part of GRUB also get installed to the actual partition being used as well???

will the breezy grub part no conflict with the dapper grub part?

sorry, i really have no idea about grub..

---

### Post by pranav on 2006-04-09
Yes indeed.. the new GRUB files will be on the new partition whr u install dapper.

The old grub files will be on the breezy partition.

However.. the new dapper install will rewrite GRUB in the MBR which will direct to the files in the dapper partition.. so your menu.lst will be from the dapper partition

During Dapper install, the GRUB will automatically detect the installed OS n configure it.

---

### Post by renzokuken on 2006-04-09
[QUOTE=pranav]Yes indeed.. the new GRUB files will be on the new partition whr u install dapper.

The old grub files will be on the breezy partition.

However.. the new dapper install will rewrite GRUB in the MBR which will direct to the files in the dapper partition.. so your menu.lst will be from the dapper partition

During Dapper install, the GRUB will automatically detect the installed OS n configure it.[/QUOTE]


cool thanks.......thats exactly what i needed to know....

although gonna have to put it on the backburner for a few days, my PSU blew up last night so i cant even turn my PC on till i replace it.......ironically, it pretty much answers this thread i started [http://www.ubuntuforums.org/showthread.php?t=155090](http://www.ubuntuforums.org/showthread.php?t=155090) ........using it now with dapper

---

