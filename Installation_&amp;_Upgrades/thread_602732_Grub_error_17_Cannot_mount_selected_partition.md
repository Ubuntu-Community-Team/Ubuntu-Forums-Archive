---
title: "Grub error 17: Cannot mount selected partition"
date: 2007-11-04
forum: Installation &amp; Upgrades
---

### Post by xcusmwah on 2007-11-04
When I restart Ubuntu I have to setup Grub each time to tell it which hard drive to boot to.  Here are the steps that I have to take:

[LIST]
[*]Press any key
[*]Hit "E"
[*]Hit "E" again
[*]Change HD1,0 to HD0,0
[*]Hit enter
[*]Hit "B" to boot into Ubuntu
[/LIST]

I'm obviously still a Ubuntu/grub newbie so I would appreciate anyone that can help me make the system change the setting permanently.  Thank you very much!

---

### Post by Pumalite on 2007-11-04
Backup first:
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.back
gksudo gedit /boot/grub/menu.lst
Make the changes in each Ubuntu entry in the 'root' line
Save, exit, reboot.
(you could change 'kopt' too)

---

