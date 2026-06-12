---
title: "Dual-Boot Problems with Vista/Ubuntu - Reinstall wanted"
date: 2010-05-24
forum: Installation &amp; Upgrades
---

### Post by aahernan on 2010-05-24
I have Ubuntu 10.04 installed on my HP HDX 18t laptop. I was also using Vista in dual-boot. Since the upgrade to 10.04 however, Vista fails to load. I get the GRUB menu(which at this point has 8 Ubuntu boot options- extremely annoying) but if I select Vista(either one of the 2 options I have SDA1 or SDA2) all I get is a black screen with an underscore in the top right corner blinking. I have waited and tried everything I can think of to get it to go past there but have had no luck.

Does anyone have any suggestions on what I can do to get Vista working? Let me know if you need more info. I want to get Vista running to back up my files and then wipe my computer clean with a factory reset to get rid of Ubuntu.

Thanks!

---

### Post by darkod on 2010-05-24
If you want to make vista boot, you will probably need to do this fix on /dev/sda2, that means partition #2 on disk /dev/sda:
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

Usually /dev/sda1 would be your restore partition, not your vista. So if you want access to the restore partition too, so you can restore the hdd to factory settings, do that procedure again for /dev/sda1.

Also, if you only want to backup files, you can see all partition from ubuntu live mode, or from ubuntu booted up. That should allow you to copy everything you want.

You can reinstall if you have vista dvd without doing the above fixes. But if the restore partition is needed, you'll have to fix it at least.

---

