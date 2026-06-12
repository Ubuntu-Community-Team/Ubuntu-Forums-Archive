---
title: "Changing Boot Menu Order"
date: 2009-12-19
forum: Installation &amp; Upgrades
---

### Post by El Conjunto on 2009-12-19
[SIZE=3]I'm a total newbee and have just installed Ubuntu 9.10 as a dual boot with Windows 7. Is there anyone out there who can write an exact script with instructions so I can edit the boot menu to default boot to Windows 7? Thanks![/SIZE]

---

### Post by Puck7 on 2009-12-19
You can try this thread, it explains more than you need, but it's probably better that way:
[http://ubuntuforums.org/showthread.php?t=1302743](http://ubuntuforums.org/showthread.php?t=1302743)

---

### Post by jerrrys on 2009-12-19
i dont think startupmanager works the same in 910, but u can load it and find out.

as for post#2, be careful with sudo, it can be deadly

[http://ubuntuforums.org/showthread.php?t=927377](http://ubuntuforums.org/showthread.php?t=927377)

---

### Post by oldfred on 2009-12-19
This is the easiest way:

If you refer to Windows by its number, you will have to edit on every update. But Grub 2 also lets you use the title. Suppose your Windows title is "Windows Vista (on /dev/sda1)". Then you can use in /etc/default/grub, and you won't have to edit Grub after kernel updates.

Copy your windows entry from this:
gedit /boot/grub/grub.cfg
Open up this file and paste entry where the 0 is:
gksudo gedit /etc/default/grub
Change GRUB_DEFAULT=0 to your windows entry like this as example
GRUB_DEFAULT="Windows Vista (on /dev/sda1)"
then run this:
update-grub

---

