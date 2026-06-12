---
title: "Moving dual boot ubuntu to seperate partition"
date: 2012-05-18
forum: Installation &amp; Upgrades
---

### Post by kenyard on 2012-05-18
ok so i have ubuntu dual booted with windows.
im upgrading windows now, or reinstalling it whichever as it needs to be done.. its gone slow as crap
im wondering can i do this without impacting ubuntu>? or should i move ubuntu to a new partition and just dual boot them from there first? (i ready a bit on this and its no biggie about impacting windows when i move it as im reinstalling that anyway, i just want to know how i move ubuntu (just copy and paste?) and how to re-enable the option of which will start on bootup)
I kinda feel i should also format the partition before my reinstall so am tempted towards the option of second partition....
im just looking for some advice on how to do it. thanks

---

### Post by darkod on 2012-05-18
Hold on, are you talking about wubi installed inside windows?

Because you mention dual boot but people wouldn't usually call that dual boot. On the contrary, having ubuntu on a separate partition as a proper dual boot is what would be called dual boot.

And try to use wubi (if that's what you have) instead of ubuntu because they work in different way and it would help people make the difference.

If it's already dual boot on separate partitions you don't need to do anything before installing windows.

On the other hand, if it's wubi, it will probably get lost especially if you format C: and install clean windows. Because it's installed like a program in windows and that way you lose all programs.

If you only do upgrade, I guess it should stay there, like the other programs.

---

### Post by bcbc on 2012-05-18
If you have a Wubi install, then it's a good time to [migrate]("https://help.ubuntu.com/community/MigrateWubi") it, prior to reinstalling windows. You'll need to restore the grub bootloader afterwards as Windows will replace it.

If this isn't what you meant by 'moving it', i.e. you want to still use wubi but on a different partition, this is possible but requires a little fiddling. Post back for more info.

---

