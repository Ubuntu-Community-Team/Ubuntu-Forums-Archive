---
title: "Downgrade from 2.6.20 to 2.6.17"
date: 2007-08-12
forum: Installation &amp; Upgrades
---

### Post by onegreenparker on 2007-08-12
I need to downgrade from 2.6.20 to 2.6.17.
How is this done?

If you would like to know why I need to do this please see this [=http://ubuntuforums.org/showthread.php?p=3170794#post3170794](=http://ubuntuforums.org/showthread.php?p=3170794#post3170794) thread

---

### Post by louieb on 2007-08-12
Do you Still have the 2.6.17 kernel listed in the GRUB menu? If so just highlite and press enter.

---

### Post by onegreenparker on 2007-08-12
I´ve installed the 2.6.17 kernel but it does not appear in the GRUB menu.
Any ideas?

---

### Post by louieb on 2007-08-12
1st check /boot to see if these 3 files are there.[LIST]
[*]System.map-2.6.17-##-386
[*]initrd.img-2.6.17-##-386
[*]vmlinuz-2.6.17-##-386[/LIST]the stuff after the 2.6.17 may not be the same as my example.

Then edit /boot/grub/menu.lst.

press Alt+F2 and enter ```
gksudo gedit /boot/grub/menu.lst
```and create a entry for the 2.6.17 kernel. Just  use one of the other kernel entries as a template. The dual boot link in my signature has some example Grub entries also.

---

