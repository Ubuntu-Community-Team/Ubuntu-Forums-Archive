---
title: "grub default not working after Ubuntu upgrade"
date: 2011-07-10
forum: Installation &amp; Upgrades
---

### Post by schwain on 2011-07-10
After upgrading my PC from 10.04 to 11.04, the grub2 default option stopped working. When grub starts up, it always highlights and boots to the first entry. I first tried using "startup-manager" to change it (which always worked before). This allowed me to change the timeout, but not the default OS. Then I changed the "GRUB_DEFAULT" option in /etc/default/grub, did the "sudo update-grub", to no effect. I next tried setting "GRUB_SAVEDEFAULT=true" in /etc/default/grub, did the update-grub, and manually booted it one time from the OS I wanted. Afterwards, it still didn't work.

I checked my grub.cfg file after each update operation, and it is refreshed each time. Inside the file, there is a line setting the default variable to 6 (the OS I want), though the default variable doesn't get used elsewhere in the file (I'm guessing something else reads grub.cfg in?). Everything else in grub still seems to be working. Once I manually point to the OS I want, the proper one always boots. My /boot is on a separate ext2 partition.

Is there any debug I can do? Anybody got any ideas about what I can try?

---

### Post by drs305 on 2011-07-10
Natty uses Grub 1.99RC, which introduced 'submenus'. Now the first kernel (and rescue mode if enabled) are displayed on the main menu and the other kernels are located in a submenu.

This action throws off the old numbering system. I wrote a guide about how to use the new submenu hierarchy:
[Grub 1.99 Submenus]("http://ubuntuforums.org/showthread.php?p=10720316#post10720316")

---

### Post by schwain on 2011-07-12
Yup, it was a numbering problem. When I first used startup-manager, it miscalculated the entry number I wanted as 6 (which didn't exist) instead of the correct 5, and I blindly used 6 later on (it doesn't help that grub numbering is 0-based). Apparently grub will just default to entry 0 when the default value doesn't exist.  The website for startup-manager does state that it currently doesn't fully support grub2 yet, though they're working on it.

---

