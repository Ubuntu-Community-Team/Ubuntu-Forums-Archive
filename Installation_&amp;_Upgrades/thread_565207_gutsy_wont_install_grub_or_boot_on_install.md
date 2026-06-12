---
title: "gutsy wont install grub or boot on install"
date: 2007-10-02
forum: Installation &amp; Upgrades
---

### Post by monkotronic on 2007-10-02
i booted from the livecd with no problems.  ran install and it seems to finish with no announcements of any kind but does not create a /boot/grub/menu.lst file.  i have tried it twice with the same result.  so, i installed grub manually and entered the info for my partition.  not when i select the option at the menu, i get this:

starting up
[ 21.982707] kernel panic - not syncing : vfs : unable to mount root fs on unknown-block (0,0).

this is my menu.lst file:
---------------------------------------------------------------------------------------

default		0
timeout		10

title		Ubuntu gutsy (development branch), kernel 2.6.22-12-generic 6,7
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.22-12-generic root=/dev/hda7 ro quiet splash acpi=force

-----------------------------------------------------------------------------------------

what should i try?

---

### Post by precinto on 2007-10-03
Same problem here.  I'll try installing GRUB manually, if I get the same problem I¡d try with this:

[http://ubuntuforums.org/showpost.php?p=2720070&postcount=2](http://ubuntuforums.org/showpost.php?p=2720070&postcount=2)

Let me know if it works.

---

### Post by precinto on 2007-10-04
Got it!

It's a problem with Migration Assistant.  Just reinstall, but don't use the desktop Install icon, instead open a terminal and do:
> 
sudo ubiquity --no-migration-assistant

---

