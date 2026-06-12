---
title: "Installation complete and Blinking Cursor after choosing OS from grub menu"
date: 2009-12-16
forum: Installation &amp; Upgrades
---

### Post by techbeam on 2009-12-16
Iam a newbie to Ubuntu.

Downloaded .iso from torrents.Check sum was matching for .iso

Installed from CD and chose options noapic and lapic no on install screen.

Installation was complete and required to reboot.

On reboot, I clicked on first option Linux Generic OS and got a blinking cursor.Waited for 30 min and no activity.

On grub menu choosing XP Pro boots fine(Xp on -dev/sda1 and no issues with booting XP.

I tried"press e" for edit and there was the following info for Generic Linux boot option

"record fail=1
if have grub-----
set root=(hd0,8)---
-------quiet splash"

Please some one help

---

### Post by darkod on 2009-12-16
It can be video driver issue but I still haven't figured out if that's always the case. You could try updating your driver if using ATI/Nvidia. Instead of the normal mode entry for ubuntu, in grub menu select recovery mode. In the next menu select something like "root with networking" to give you internet access. When the command prompt loads install EnvyNG package with:
sudo apt-get install envyng-core envyng-qt

Run it in text mode with:
envyng -t

In the menu there is option to remove current driver but not needed to do this. Just select the manufacturer and follow the process, it downloads the driver itself. After installation is finished it will ask to reboot.
After the reboot check if the normal mode entry will work OK.

---

### Post by techbeam on 2009-12-17
Thanks for the tips.On recovery mode i get error "tsc clock source unstable" and hangs @ this point

---

